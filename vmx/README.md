vrnetlab / Juniper vMX
========================
This is the vrnetlab docker image for Juniper vMX.

Building the docker image
-------------------------
Download vMX from http://www.juniper.net/support/downloads/?p=vmx#sw
Put the .tgz file in this directory and run `make` and you should be good to
go. The resulting image is called `vr-vmx`. You can tag it with something else
if you want, like `my-repo.example.com/vr-vmx` and then push it to your repo.
The tag is the same as the version of the JUNOS image, so if you have
vmx-15.1F4.15.tgz your final docker image will be called vr-vmx:15.1F4.15.

Usage
-----
The container must be `--privileged` to start KVM.
```
docker run -d --privileged --name my-vmx-router vr-vmx
```
It takes about TBD seconds for the virtual router to start and after this we can
login over SSH / NETCONF with the specified credentials.

If you want to look at the startup process you can specify `-i -t` to docker
run and you'll get an interactive terminal, do note that docker will terminate
as soon as you close it though. Use `-d` for long running routers.

The vFPC has a serial port that is exposed on TCP port 5001. Normally you don't
need to interact with it but I imagine it could be useful for some debugging.
