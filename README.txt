Use this to build a Docker image based on Red Hat UBI-7
image with Shaw's self-signed certificate and some basic
networking utilities packages (net-tools, iproute, iputils).

Test TLS/SSL connectivity using curl:

  curl https://www.google.com


Test networking tools:

   ip addr show
   ping www.google.com

Notes:

this repository is optimized for a Windows Pro OS Build 10.0.18363, Version 1909 with Windows Subsystem
Linux 2 (WSL2). You will need to run the install as an Administrator, and may have to modify or disable 
any or all security/firewall specifications for your machine in order to allow the container to retrieve
its required data. 

The current Dockerfile build data is customized with certifications to allow some security features to 
remain enabled while simultaneously not causing the container instantiation to fail. 

Kubernetes should be v1.19.3+

  First, you will need to verify you have Docker Desktop Installed. You will need to create an account, 
  install, re-log in, and restart your machine.  The newest version of Docker Desktop has Experimental 
  Features, of which the Cloud Experience should be enabled. Also, it might be wise to enable all options 
  in the Docker Desktop Settings General Section. 

