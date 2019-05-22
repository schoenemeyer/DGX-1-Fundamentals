
# DGX-1-Fundamentals  Quick User Guide 

This quick guide is useful for clients that start working with NVIDIA DGX-1 and want to move forward as quick as possible.
All the information below is public. There is also a 90sec video on youtube available for a quick overview      
https://www.youtube.com/watch?v=fAZS4V2aolI. 

![After processing](https://github.com/schoenemeyer/DGX-1-Fundamentals/blob/master/figures/maxresdefault.jpg)

## Install, Provisioning, Networking, NFS Mount  
https://docs.nvidia.com/dgx/dgx1-user-guide/index.html    
or as pdf (May 2019)    
https://images.nvidia.com/content/technologies/deep-learning/pdf/DGX-1-UserGuide.pdf

General recommendation:   
Use a separate, firewalled subnet and configure a separate VLAN for BMC traffic if a dedicated network is not available
Make sure proxy settings are done properly for the OS version.
For Ubuntu 18.0.4: in diretory /etc/systemd/system/docker.service.d we need 3 files , http-proxy.conf, https-proxy.conf and no-proxy.conf.
Make sure you can connect with http://security.ubuntu.com/ubuntu


## Basic Health Checks 

sudo nvsm show health

![After processing](https://github.com/schoenemeyer/DGX-1-Fundamentals/blob/master/figures/dgx-1.JPG)

## Learn how to use NGC
https://docs.nvidia.com/dgx/ngc-registry-for-dgx-user-guide/index.html

## Go directly to NGC
https://ngc.nvidia.com/catalog/landing

## DGX-1 System Architecture
https://docs.nvidia.com/dgx/dgx-os-server-release-notes/index.html
https://indico.desy.de/indico/event/21640/session/1/contribution/15/material/slides/0.pdf


## V100 Architecture
https://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf

## DGX OS Server  
https://docs.nvidia.com/dgx/dgx-os-server-release-notes/index.html

## Application Performance with multiple GPUs (and multiple nodes)
https://github.com/horovod/horovod

## DGX Benchmarks
https://developer.nvidia.com/deep-learning-performance-training-inference

## AMP
Reduce runtimes with mixed precision (FP16/FP32)   
https://devblogs.nvidia.com/nvidia-automatic-mixed-precision-tensorflow/

## Your way from single GPU to multi GPU to multi GPU multi node
http://on-demand.gputechconf.com/gtc-cn/2018/pdf/CH8209.pdf

## Kubernetes
Cluster deployment with Kubespray (Open Source)
https://github.com/kubernetes-sigs/kubespray
or DeepOps (Open Sourced, supported by NVIDIA) for large-scale  DGX Cluster deployments
https://github.com/NVIDIA/deepops

## Use Polyaxon for traceable results

Use Polyaxon for rproducible Result
https://docs.polyaxon.com/concepts/tensorboards/

and for hyperparameter research
https://docs.polyaxon.com/concepts/tensorboards/


