# nvidia-problemsfor2days
I experienced a suck problems and finally find the solution


Days ago, I met a hard problem . It made me reinstalled my ubuntu system.However,no matter how I installed the vidia-drivers can not load my nvidia-drivers.
So if you are preparing for a new ubuntu+nvidia+cuda,I suggest you follow my steps:

1. Install your ubuntu and restart when your installation is finished.

2. As far as you log in the new system,you'd better open your commandline and input:

sudo apt-get update (As a newly installed system,you don't have any soft wear in you list)

3.Take the damn nouveau to the black list like:
sudo gedit /etc/modprobe.d/blacklist.conf
add:
blacklist nouveau
options nouveau modeset=0
save then input:
sudo update-initramfs -u
(if you don't complete this step ,you will shutdown suddenly whenever you click settings)
4.download cuda-tool-kit runfile on the website
5.Don't forget download some libraries:
sudo apt-get install buil-essential
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev freeglut3-dev libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
sudo apt-get install --no-install-recommends libboost-all-dev
sudo apt-get install libopenblas-dev liblapack-dev libatlas-base-dev
sudo apt-get install libgflags-dev libgoogle-glog-dev liblmdb-dev
(I skip these and only installed build-essential ,then it cost me 2 days to check logs.It drives me crazy.)
Afterthat, do the install like:
sudo sh XXXX.run
Finally,do:
sudo nvidia-smi
make sure that it works correctly.
