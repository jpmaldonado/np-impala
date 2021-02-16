# Impala for Business Intelligence 
2-day course on Apache Impala (formerly Cloudera Impala)

## Getting started

Cloudera killed the official support for the Quickstart VM. However, according to [this](https://community.cloudera.com/t5/Support-Questions/Cloudera-Quickstart-VM-Download/td-p/291225) blog post in Cloudera community, you can still download it from these links:

- [Virtualbox](https://downloads.cloudera.com/demo_vm/virtualbox/cloudera-quickstart-vm-5.12.0-0-virtualbox.zip)
 
- [VMWare](https://downloads.cloudera.com/demo_vm/vmware/cloudera-quickstart-vm-5.12.0-0-vmware.zip)

### Plan B: Docker

The docker image is *not* officially supported. But it is not hard to get it started.

#### Steps
- Get a Linux machine with 100 GB hard drive and 8 GB RAM (or 16 GB if you plan to use Cloudera Manager too).
- All following commands must be typed in the terminal.
- You need to install `docker`:
	- `yum install docker` (CentOs) 
	- `apt-get install docker` (Ubuntu)
- After installing, pull the docker image:
`docker pull cloudera/quickstart:latest`
- Use `docker images` to get the hash of your image. The first four digits are enough. My image hash started with 4239cd, so the command is:
`docker run --hostname=quickstart.cloudera --privileged=true -it -p 8888:8888 -p 7180:7180 -p 80:80 -p 25000:25000 4239cd /usr/bin/docker-quickstart`

This habilitates the following ports:
- 8888: Port for Hue (Impala Query Editor).
- 7180: Port for Cloudera Manager.
- 25000: Port for Impala WebUI.
- 80: Port for a short tutorial.
Adjust the command accordingly. If you only want Hue, you can remove all the other options under the `-p` flag.

#### (Optional) If you want to use Cloudera Manager

Once everything is up and running type the following command in the quickstart terminal:

`./home/cloudera/cloudera-manager --express`

Wait a little bit and you should be able to access

Issue the command `service ntpd restart` in the quickstart shell. This gets rid of a timezone conflict.



 

## References
- [Getting Started with Impala](https://www.amazon.com/Getting-Started-Impala-Interactive-Apache/dp/1491905778/)
- [Quickstart VM Docker Image](https://docs.cloudera.com/documentation/enterprise/5-6-x/topics/quickstart_docker_container.html)

