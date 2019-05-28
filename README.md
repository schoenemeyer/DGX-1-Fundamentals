
# DGX-1-Fundamentals  Quick User Guide 

This quick guide is useful for clients that start working with NVIDIA DGX-1 and want to move forward as quick as possible.
All the information below is public. There is also a 90sec video on youtube available for a quick overview      
https://www.youtube.com/watch?v=fAZS4V2aolI. 

![After processing](https://github.com/schoenemeyer/DGX-1-Fundamentals/blob/master/figures/maxresdefault.jpg)

## Install, Provisioning, Networking, NFS Mount  
The User Guide is available as web version: https://docs.nvidia.com/dgx/dgx1-user-guide/index.html    
or as pdf (May 2019)    
https://images.nvidia.com/content/technologies/deep-learning/pdf/DGX-1-UserGuide.pdf

General recommendation:   
Use a separate, firewalled subnet and configure a separate VLAN for BMC traffic if a dedicated network is not available
Make sure proxy settings are  properly set.     
### Networking

1. Basic Setting: Be aware of the new network interface in ubuntu 18.04 

If you go through the standard setup and provide  ip address, gateway, nameserver and domain name , you can proceed with proxy settings.
If you have to change any details afterwards, you can edit /etc/netplan/01-netcfg.yaml. 
To apply the changes, please use  
```
sudo netplan apply
```
For further questions visit https://www.tecmint.com/configure-network-static-ip-address-in-ubuntu/ for more details

2. System-wide Proxy Settings 

Add System-wide Proxy Settings in /etc/environment  
```
http_proxy="http://<username>:<password>@<hostname>:<port>/"    
https_proxy="http://<username>:<password>@<hostname>:<port>/"   
ftp_proxy="http://<username>:<password>@<hostname>:<port>/"    
no_proxy="<pattern>,<pattern>,...
```  
3. Configuring Proxy for APT

Aptitude will not use the HTTP Proxy environment variables. Instead, it has its own configuration file where you can set your proxy.
Create a file /etc/apt/apt.conf.d/proxy.conf and add following lines, using the parameters that apply to your network:
```
Acquire::http::proxy "http://<username>:<password>@<host>:<port>/"; 
Acquire::ftp::proxy "ftp://<username>:<password>@<host>:<port>/"; 
Acquire::https::proxy "https://<username>:<password>@<host>:<port>/";
```
4. Configure Proxy for docker

For Ubuntu 18.0.4: in directory /etc/systemd/system/docker.service.d we need 3 files. If the directory does not exist, you have to create it.

1. http-proxy.conf, 
2. https-proxy.conf 
3. no-proxy.conf 

Here is an example for http-proxy.conf
```
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/"
```
and for https-proxy.conf
```
[Service]
Environment="HTTPS_PROXY=http://proxy.example.com:80/"
```
Test with 
```
docker run hello-world 
```

Make sure you can connect with http://security.ubuntu.com/ubuntu
For questions regarding docker you can consult:
https://docs.docker.com/config/daemon/systemd/


## Basic Health Checks 

sudo nvsm show health

![After processing](https://github.com/schoenemeyer/DGX-1-Fundamentals/blob/master/figures/dgx-1.JPG)

## Learn how to use NGC

Typically you will use the DGX Family with a docker environment; it is installed with the OS per default. 
You dont have to install anything else, as long as the docker environment is up and running.      
With NGC you always get the latest and fastest implementation for your DGX hardware just in minutes    
https://docs.nvidia.com/dgx/ngc-registry-for-dgx-user-guide/index.html

For individual frameworks please refer to the NVIDIA documentation    
https://docs.nvidia.com/deeplearning/dgx/tensorflow-user-guide/index.html#custtf


## Go directly to NGC
https://ngc.nvidia.com/catalog/landing

## DGX-1 System Architecture
https://docs.nvidia.com/dgx/dgx-os-server-release-notes/index.html
https://indico.desy.de/indico/event/21640/session/1/contribution/15/material/slides/0.pdf


## V100 Architecture
https://images.nvidia.com/content/volta-architecture/pdf/volta-architecture-whitepaper.pdf

## DGX OS Server  
A DGX Server is usually preloaded with an OS. For learning about the background and options for OS versions, please visit    
https://docs.nvidia.com/dgx/index.html

The current release information is 4.1 (May 2019) and can be found here:      
https://docs.nvidia.com/dgx/dgx-os-server-release-notes/index.html     
The NVIDIA® DGX™ servers (DGX-1 and DGX-2) are shipped with DGX™ OS which incorporates the NVIDIA DGX software stack built upon the Ubuntu Linux distribution. Instead of running the Ubuntu distribution, you can run Red Hat Enterprise Linux onthe DGX system and take advantage of the advanced DGX features. Please see https://docs.nvidia.com/dgx/index.html.    
The full install guide as pdf:     
https://docs.nvidia.com/dgx/pdf/dgx-rhel-install-guide.pdf

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

## Need more local storage capacity

no problem, NVIDIA has offerings with 5 major storage vendors, please visit for more details 

https://blogs.nvidia.com/blog/2019/03/18/roi-ai-data-center-leaders-dgx-pod/



