# Structured Prediction Helps 3D Human Motion Modelling
> ### Emre Aksan, Manuel Kaufmann, Otmar Hilliges

![Network](/assets/spl_models.png)



### Architecture

| Network | Input | Output |
| :---: | :---: | :---: |
    


## Challenge

- Modeling human motion is has many applications:
    - Human computer interface
    - Human detection and tracking
    - Image based pose estimation in the context of robotics or self-driving vehicles.
- Despite recent progress in data-driven modelling of human motion, this task remains challenging for machines.
- The difficulty of this task is manifold:
    - Human motion is highly dynamic, non-linear, and becomes more stochastic overtime with a high-degree of inherent uncertainty.
    - Humans leverage strong structural and temporal priors about continuity and regularity in natural motion. However these are hard to model algorithmically due to:
        - Inter-dependencies between joints
        - Influence of high-level activities on the motion sequences (transition from walking to jumping). 
- Early works (ERD, SRNN) focused on RNN using curriculum learning scheme to increase robustness to temporal drift. 
- Martinez _et al._ __[GRU_martinez]__ shown that a simple running-average provides a surprisingly  difficult to beat baseline in terms of Euler angle error. 
    - Adversarial training was also used to address the drifting problem.
    - Pavllo _et al._ studied the impact of joint angle representation and show that a quaternion-based parameterization improves short-term predictions.
- However quantitative performance does not translate to qualitatively meaningful prediction. Furthermore, the H3.6M benchmark is becoming saturated, limiting progress.
- __Main challenge:__ 
    - How to measure accuracy of pose prediction in a meaningful way so low errors correspond to good qualitative results, which also leads to a good network guide.
    - How to exploit spatial structure of the human skeleton for better predictions?



## Solution

- Used AMASS as it is bigger and a wider range of activities compared to Human3.6M. 
    - Also introduced several evaluuation metrics to the task of human motion prediction.
- Proposed __Structured Prediction Layer__ (SPL) to address 2nd problem.
    - The layer leverage the compositional structure of the human skeleton by explicitly decomposing the pose into individual joints.
    - SP-layer models the structure of human skeleton, hence the spatial dependencies between joints.
    - Each node in the graph receives information about the parent node's prediction and thus information is propagated along the kinematic chain. 
    - Introduced a new joint-wise decomposition of the loss function as part of SPL.
        - This part is agnostic and can be applied to most existing architectures.
        - Claimed that introducing this layer to existing approaches improves performance. While the impact is more noticable on bigger and more challenging dataset.



## Notes

- New metric used:  
    - __Joint angle difference__: Computes the angle of the rotation required to align the predicted joint with the target joint.
    - __Positional__: Performs forward kinematics on the predicted joints to obtain 3D joint positions. Then compute euclidean distance per joint.
    - __PCK__: In case L<sub>pos</sub> has large error, compute the percentage of predicted joints lying within a spherical threshold around the target joint position.



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



### Read Related Works!



## Results

|![Metric1](/assets/spl_metric_h36m.png) | 
| :--: | 
| __Human3.6m metric result__ |


| ![Metric2](/assets/spl_metric_amass.png) | 
| :--: | 
| __Amass metric result__ |

