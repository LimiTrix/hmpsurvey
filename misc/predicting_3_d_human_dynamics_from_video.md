# Predicting 3D Human Dynamics from Video
> ### Jason Y. Zhang, Panna Felsen, Angjoo Kanazawa, Jitendra Malik

![Network](/assets/phd_models.png)



### Architecture

- Movie Strip encoder:
    | Network | Input | Output |
    | :---: | :---: | :---: |
    | __Resnet50__ | Image  | image features |
    | __Causal Temporal Encoder (f<sub>movie</sub>)__   | Image features | Movie strips |
- Prediction net:
    | Network | Input | Output |
    | :---: | :---: | :---: |
    | __TCN (f<sub>AR</sub>)__ | Movie strips | Future movie strips | 
    | __3D Regressor (f<sub>3D</sub>)__ | Future movie strips | 3D SMPL param |



## Challenge

- __Main motivation:__ Existing works predict 3D future from 3D past or 2D future from 2D past input. 
    - No work tackled prediction problem from 2D past input to 3D future. 
    - Most works focus on predicting 2D components from video such as 2D keypoints, flow, or pixels.
    - While works that focus on 3D human prediction take past 3D skeleton sequences as input from mocap data.
- Practical applications including:
    - Autonomous systems that must opperate safely around people from visual input (e.g., self-driving cars, drones).
- States that interest in modeling human dynamics has appeared as early as [1997](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=609382)



## Solution

- Proposed a method that builds upon authors previous work that learns a latent representation for 3D human dynamics from the temporal context of image frames. 
    - The proposed method changed the scope of the prediction into causal where before it was a combination of both future and past information.
- After learning a causal latent representation for 3D human motion from video, they train an autoregressive prediction model in this latent space.
- Stated that authors proposed method can recurrently predict a longer range future that is more stable by taking advantage of a sequence of past images.



## Notes

- Showed a paper that stated prediction result in Human3.6m does not correlate with challenging in-the-wild video datasets such as 3DPW ([Source 1](https://virtualhumans.mpi-inf.mpg.de/papers/vonmarcardECCV18/vonmarcardECCV18.pdf), [Source 2](https://arxiv.org/pdf/1812.01601.pdf)).
- Mentioned a technique to more accurately evaluate prediction result called __Dynamic Time Warping__
    - Further explained in the supplementary material.



## Dataset 

Trained jointly in an _**action-dataset-agnostic**_ manner
- **Human3.6M**: 
    - Contains _**GT 3D annotations**_
    - Training: Subject 1, 6, 7, 8 
    - Validation: Subject 5
    - Testing: Subject 9 and 11
- **Penn Action**: 
    - Contains _**GT 2D keypoint annotation**_
- **NBA**: 
    - Contains _**GT 2D keypoint annotation**_
    - Dataset from authors previous works
- **InstaVariety**
    - Using _**pseudo-GT using 2D keypoint annotations from OpenPose**_



## Results

Mostly ablation because lack of previous works.
![Metric](/assets/phd_metric.png)