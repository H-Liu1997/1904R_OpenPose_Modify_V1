# 1904_research_OpenPose_modification_version1
==== 2012 update ====
This code commemorates my first official research topic. The code is not related to the work in my publication at all.  
## Encoding method
### Parameters
This encoding method of this model have `5` parameters:<br>
`PAF_detax_19channels`<br>
`PAF_datay_19channels`<br>
`Capsule_centerx_19channels`<br>
`Capsule_centery_19channels`<br>
`Capsule_length_19channels`<br>
### Groundtruth 
Range of PAF:<br>
[-1,+1]<br>
Range of centerx and centery and length:<br>
[0,1]<br>
    <br>
The groundtruth image:<br>
![](https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/groundtruth.png)
![](https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/groundtruth_0.png)
![](https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/groundtruth_1.png)
![](https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/groundtruth_2.png)
## Network
This model use the openpose network and change the input channels.<br>
The PAF is in branch 1.<br>
Total channel `38`.<br>
The Capsule is in brance 2.<br>
Total channel `57`.<br>
## Training results
Total time: `4`days for 1 day in GTX 1080Ti and 3 days in GTX 1080.<br>
Epoch:`56`.<br>
The details is in training/`training.csv`<br>
    <br>
Loss Graph:<br>
![](https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/loss.png)<br>
    <br>
Results:<br>
<img src="https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/centerx.png" width="300" height="300" alt="centerx"/>
<img src="https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/centery.png" width="300" height="300" alt="centery"/><br>
<img src="https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/length.png" width="300" height="300" alt="length"/>
<img src="https://github.com/HaiyangLiu1997/Model_V1_BC_0409_2019/raw/master/result_images/paf.png" width="300" height="300" alt="PAF"/><br>
## Results analysis
### Why give up
The centerx and centery need the network learns grobal information, consider remove it.<br>
It's hard to make sure the real center points, because the network output have a smooth change.<br>
    The max output is larger than the centerx and centery.<br>
    The range is form 0 to max.<br>
### Accuracy
Haven't test.<br>
## How to use this model
For training:<br> 
Open the training file, change the dataset path in:<br>
`train_pose.py`<br> 
`dataset.py`<br>
If restart training, run `train_pose.py`.<br>
If continue training, get `weight.best.h5` first.<br>
https://1drv.ms/u/s!AmvJMVSfZX21kA3e9rtSRLPw7L0D<br>
For test result:<br>
Get the `weight.best.h5` first.<br>
Open the `demo.ipynb` with jupyter notebook or colab.<br>
Run the ipynb code step by step.<br>
