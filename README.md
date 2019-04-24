# Model_V1_BC_0409_2019
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
Loss Graph:<br>
Results:<br>
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
