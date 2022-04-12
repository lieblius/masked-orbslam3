# Masked ORB-SLAM3

This is Team 6's final project git repository for EECS 568: Mobile Robotics. The title of our project is Masked ORB-SLAM3: Dynamic Element Exclusion for Autonomous Driving Scenarios Using Masked R-CNN for Increased Localization Accuracy. Our team members include: [Aditya Om](https://www.linkedin.com/in/adityaom/), [Aman Kushwaha](https://www.linkedin.com/in/aman-kushwaha-19b4681b1/), [Kyle Liebler](https://www.linkedin.com/in/lieblius/), [Ping-Hua Lin](https://www.linkedin.com/in/michaelphlin/) and [Zhuowen Shen](https://www.linkedin.com/in/zhuowenshen7558/).

You can see the mask used for our Masked ORB-SLAM running here: 
<p align="center">

![KITTI mask](media/mask_KITTI.gif)
</p>

You can also see our implementation running here:

<p align="center"> ![KITTI mask](media/demo.gif =900x510) </p>

## Getting Started

First, we recommend you read through our paper uploaded on this repository/docs. Next, read the two directly related works: [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3?msclkid=d3a88f5eb81f11ec968f0535c7080186) and [DynaSLAM](https://github.com/BertaBescos/DynaSLAM?msclkid=fe9695b7b81f11ec9d82fc4c92af772c)..

### Masked ORB-SLAM3 Architecture
<p align="center">
 ![ORB-SLAM3 Architecture](media/masked_orbslam_arch2.png)
</p>

## Project Overview

To observe and remove the impact of dynamic objects in ORB-SLAM3 we selected one of the most dynamic datasets from the KITTI datasets. We observed that the ORB-SLAM 3 performs better if the dynamic content from the image frames is removed. We remove dynamic objects from the images by performing instance segmentation and then passing binary masks into the ORB-SLAM3 pipeline. We then use these masks to remove tracking points that overlap with our masks.


---
### Running the Docker Image

This docker is based on ros melodic ubuntu 18.

There are two versions available:
- CPU based (Xorg Nouveau display)
- Nvidia Cuda based. 

To check if you are running the nvidia driver, simply run `nvidia-smi` and see if get anything.

Based on which graphic driver you are running, you should choose the proper docker. For cuda version, you need to have [nvidia-docker setup](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html) on your machine.

---

### Compilation and Running

Steps to compile the Orbslam3 on the sample dataset:

- `./download_dataset_sample.sh`
- `build_container_cpu.sh` or `build_container_cuda.sh` depending on your machine.

Now you should see ORB_SLAM3 is compiling. 
To run a test example:
- `docker exec -it orbslam3 bash`
- `cd /ORB_SLAM3/Examples&&./euroc_examples.sh`

---

You can use vscode remote development (recommended) or sublime to change codes.
- `docker exec -it orbslam3 bash`
- `subl /ORB_SLAM3`

---

### Running Our Implementation

Once the container can run the sample data from the instructions, you may add your own data (for example from the KITTI dataset) into the Datasets folder with the same hierarchy. To use our masked implementation, clone this repository and run the `build.sh` command. Then run `mono_kitti` (looking at `euroc_examples.sh` can show examples of how the original implementation is run) with an additional command line argument appended at the end containing the directory of the segmentation masks. If you are using WSL make sure you are running an x-server so you can see the GUI.

## Acknowledgments

Thank you to Maani Ghaffari Jadidi our EECS 568 instructor, as well as the GSIs Tzu-Yuan (Justin) Lin and Jingyu (JY) Song for all the support they provided this semester. You can find a link to our course website [here](http://robots.engin.umich.edu/mobilerobotics/).

We would like to acknowledge  Carlos Campos, Richard Elvira, Juan J. Gómez Rodríguez, José M. M. Montiel, Juan D. Tardos., for their work in ORB-SLAM3, as well as Berta Bescos, José M. Fácil, Javier Civera and José Neira for their work in DynaSLAM. 
