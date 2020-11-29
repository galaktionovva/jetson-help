# jetson-help
<br>
Start camera viewer: gst-launch-1.0 nvarguscamerasrc ! nvoverlaysink <br>
<br> 
select camera slot: nvarguscamerasrc sensor_mode=0 <br>
<br>
select capture mode:  <br>
gst-launch-1.0 nvarguscamerasrc sensor_mode=0 ! 'video/x-raw(memory:NVMM),width=3820, height=2464, framerate=21/1, format=NV12' ! nvvidconv flip-method=0 ! 'video/x-raw,width=960, height=616' ! nvvidconv ! nvegltransform ! nveglglessink -e
<br>
setup inferences:  <br>
$ sudo apt-get update<br>
$ sudo apt-get install git cmake libpython3-dev python3-numpy<br>
$ git clone --recursive https://github.com/dusty-nv/jetson-inference<br>
$ cd jetson-inference<br>
$ mkdir build<br>
$ cd build<br>
$ cmake ../<br>
$ make -j$(nproc)<br>
$ sudo make install<br>
$ sudo ldconfig<br>
<br>
 https://github.com/dusty-nv/jetson-inference/blob/master/docs/building-repo-2.md
 <br>
 
