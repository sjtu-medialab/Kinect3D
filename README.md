# Kinect3D

## System hardware architecture 

The capturing system is composed of multiple Kinect v2 sensors and a single computer. The Kinect v2 sensors are positioned on a circle of radius and oriented toward the center. In terms of the software development kit(SDK), the system uses an open-source third-party driver libfreenect2, which has been reported to support up to 5 devices through USB3.0.

<img src="https://notes.sjtu.edu.cn/uploads/upload_899d2a90d8c24c29faf61fd583934f69.png" style="zoom:80%;" />

## Pipeline design of the system

To improve the real-time performance, this system adopts a pipeline design that uses multiple threads to execute all modules concurrently. Besides, the first-in-first-out feature of the queue is utilized for data transmission and thread separation.

<img src="https://notes.sjtu.edu.cn/uploads/upload_9502d9034b21889f1cd82724fb1d5642.png" style="zoom: 40%;" />

## Removal of Overlapping Regions
<img src="https://notes.sjtu.edu.cn/uploads/upload_ee1b653348131ac9820746dcc449c7aa.png" style="zoom:50%;" />

## Reconstruction Quality
<img src="https://notes.sjtu.edu.cn/uploads/upload_3f43a3ca98e9711ea6cf7c89cf4226b8.png" style="zoom:50%;" />

## Real-time Performance

The real-time performance of the proposed system is tested by measuring the processing time of each module in the system. The experimental condition is 3 sensors and the scene size is set to 1.5m x 1.5m x 1.5m. To make the results more reliable, we capture 1000 consecutive frames and track the latency of each frame. The result is demonstrated below.  As shown in Tab.1, the camera acquisition module takes the longest time which is slightly over 33ms and the final average frame rate is calculated to be 25-27 fps.

Under normal circumstances, the interval between two frames captured by the sensor is 33ms, but in some occasional cases, the interval between two frames is 66ms or even 99ms. This is a problem caused by the hardware, so we can still state that this system achieves the inherent sensor frame rate of 30 fps in terms of real-time performance.

<img src="https://notes.sjtu.edu.cn/uploads/upload_04036f09c410eb43ec9b429b980848d8.png" style="zoom:60%;" />