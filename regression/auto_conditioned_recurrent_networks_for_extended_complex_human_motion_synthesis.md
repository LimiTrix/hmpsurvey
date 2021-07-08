# Auto-Conditioned Recurrent Networks for Extended Complex Human motion Synthesis
> ### Zimo Li, Yi Zhou, Shuangjiu Xiao, Chong He, Zeng Huang, Hao Li


![Network](/assets/ac_lstm_models.png)



## Architecture

- LSTM that feeds its prediction result as input.



## Challenge & Motivation

- Synthesis of realistic human motion has recently seen increased interest with applications 
beyond animation and video games.
- Mentions a challenge for human motion synthesis to generate new variations of motions while 
preserving a certain style (generating large numbers of different bollywood dances). 
    - Also claimed that previous works that tried to tackle this problem failed to add new variations to existing motion while trying to keep the style consistent.
    - Recent networks tried to incorporate high-level parameters (walking path) to guide the synthesizing process. They note that these networks does not generate new motion variations.
- They claim previous HMP methods produce realistic motion only until a few frames in the future. After that the motion becomes unrealistic within a couple of seconds and is unable to recover from it. 
    - They believe the reason is due to feeding the networks output back into itself.
    - There is a disrepancy as the network receives GT as input for prediction while in testing the network output becomes the input.
    - The network will encounter new distribution in test time since the input is vastly different with the one its trained with.



## Solution

- Proposed AC_RNN:
    - Compensates the distribution disrepancy in testing and training phase by feeding the prediction result back to the network (As mentioned in the [2015 paper](https://arxiv.org/pdf/1506.03099.pdf) about machine translation). 
    - Also claims the result is lightweight and can be used in conjunction with any other RNN based learning scheme.
    - Claims that the generated motion can be synthesized indefinitely without end.



## Dataset 

- **CMU Mocap** where the network is trained on each for distinct subjects separately. 
    - Martial arts
    - Indian Dance
    - Indian/Salsa Hybrid
    - Walking



## Result
__[Video](https://www.youtube.com/watch?v=FunMxjmDIQM)__
![Metric](/assets/ac_lstm_metric.png)

