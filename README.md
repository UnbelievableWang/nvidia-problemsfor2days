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

5.Don't forget download some libraries OPENGL:  

    sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev freeglut3-dev  
!!when you test lGL by run test.c , you may faild to target, a bug happens in ubuntu 18.04. I reinstalled twice and failed twice.  
It is because apt do not help us to build libGL.so in /usr/lib/. When apt completes installing, only libGL.so.1 do we have.
    cd /usr/lib 
    ln -s libGL.so.1 libGL.so
Then you can find a new file libGL.so.
(I skip these and only installed build-essential ,then it cost me 2 days to check logs.It drives me crazy.)  
Afterthat, run the install file like:  
    sudo sh XXXX.run  
Finally:  
  sudo nvidia-smi  
  make sure that it works correctly.  
