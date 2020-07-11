Use this to build a Docker image based on Red Hat UBI-7
image with Shaw's self-signed certificate and some basic
networking utilities packages (net-tools, iproute, iputils).

Test TLS/SSL connectivity using curl:

  curl https://www.google.com


Test networking tools:

   ip addr show
   ping www.google.com
