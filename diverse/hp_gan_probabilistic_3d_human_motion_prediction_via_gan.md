# HP-GAN: Probabilistic 3D human motion prediction via GAN
> ### Emad Barsoum, John Kender, Zicheng Liu

![Network](/assets/hp_gan_models.png)



## Architecture

| Name | Network |   
| :--: | :--: | 
| Generator (LSTM) | LSTM |
| Critic & Discriminator | Multilayer perceptron |



## Challenge & Motivation

- Accurate near future prediction is useful for daily-activity, social interactions, and ultimately survival
    - Vehicle movement prediction and pedestrian motion prediction is important for driving related machine, handshaking required requires prediction of the hand location, and sports could benefit from predicting other players' reactions. 
- Existing networks are deterministic by nature and is based on a modified RNN (Recurrent-Decoder) that adds FC layer before and after LSTM.
    - Author stated that predicting only a single future human pose at a time results in error drifting (where the error in curr frame will propagate to next frame). 
    - Previous method __S-RNN__, outperforms current SOTA but requires redesigning the structure graph manually and task for each task.
- However, the author claim that the main issue of deterministic prediction of human motion are:
    - Future is __not deterministic__ (except in short term). The same previous pose can lead to multiple different future pose.
    - As proven in [this paper](https://arxiv.org/pdf/1511.05440.pdf), using L2 norm in non-deterministic can cause the model to average between two possible futures. 

![Reference 1](/assets/hp_gan_ref1.png)

- At the time of writing, GANs are still difficult to train and unstable. They addressed said problem by adding a loss based on skeleton physics in addition to GAN loss.



## Solution

- Proposed HP-GAN:
    - Based on Wasserstein GAN. Calculates loss by finding the minimum cost of transporting mass in order to transform the distribution _q_ into the distribution _p_. 
- The network is trained on all action type jointly. 
- Takes a sequence of skeletal pose as input + a random vector of _z_. 
    - For each such _z_ value, the network generates different output sequences.



## Dataset 

- __NTURGB-D__: largest available RGB-D and skeleton based dataset
- __Human3.6m__: One of the largest available dataset from MoCap data.

## Read conclusion!