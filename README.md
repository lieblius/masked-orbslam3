# Masked ORB-SLAM3

This is Team 6's final project git repository for EECS 568: Mobile Robotics. The title of our project is Visual Lidar Odometry and Mapping with KITTI, and team members include: Aditya Om, Aman Kushwaha, Kyle Liebler, Ping-Hua Lin and Zhuowen Shen.

You can see the mask used for our Masked ORB-SLAM running here: 
<p align="center">
 ![alt text](media/mask_KITTI.gif)
</p>

## Getting Started

First, we recommend you read through our paper uploaded on this repository/docs. Next, read the two directly related works: [ORB-SLAM3](https://github.com/UZ-SLAMLab/ORB_SLAM3?msclkid=d3a88f5eb81f11ec968f0535c7080186) and [DynaSLAM](https://github.com/BertaBescos/DynaSLAM?msclkid=fe9695b7b81f11ec9d82fc4c92af772c)..

### Masked ORB-SLAM3 Architecture
<p align="center">
 ![ORB-SLAM3 Architecture](media/masked_orbslam_arch2.png)
</p>

## project Overview



---
### Running the docker

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

## Acknowledgments

Thank you to Maani Ghaffari Jadidi our EECS 568 instructor, as well as the GSIs Tzu-Yuan (Justin) Lin and Jingyu (JY) Song for all the support they provided this semester. You can find a link to our course website [here](http://robots.engin.umich.edu/mobilerobotics/).

We would like to acknowledge  Carlos Campos, Richard Elvira, Juan J. Gómez Rodríguez, José M. M. Montiel, Juan D. Tardos., for their original papers and source code, as well as Berta Bescos, José M. Fácil, Javier Civera and José Neira for their work in DynaSLAM. 