# Recurrent Network Models for Human Dynamics
> ### Katerina Fragkiadaki, Sergey Levine, Panna Felsen, Jitendra Malik

![Network](/assets/erd_network.png)



### Architecture

LSTM + Encoder/Decoder
Simple network for predicting motion. 



## Challenge

- First of the motion prediction algorithm.
- Compares their proposed method against motion flow based model that they "created" 
- Motivated by the importance of prediction in fields such as human-computer interaction, obstacle 
avoidance, and people tracking.
- Said that the motion of inanimate objct can be predicted using known physical laws, while
there's no physical laws that govern human motion. Hence the difficulty in prediction.



## Solution

- Proposed Encoder-Recurrent-Decoder network (Recurent network that combines representation learning
with learning temporal dynamics). 
- Applied to generation, labeling, forecasting of human kinematics.
- Encoder transforms the input data to a representation where learning of dynamics is easy. 
- Decoder transcribes the output of recurrent layer to the desired form.
- For mocap generation, __E&D = multilayer FC network__
- For video pose labeling and prediction; __E = CNN, D = FC network__.



## Notes

- We consider two data domains: motion capture (“mocap”) and video sequences. 
- For mocap, conditioning on a mocap sequence so far, we learn a distribution over mocap feature vectors in the subsequent frame. At test time, by supplying mocap samples as input back to the model, long sequences are synthesized. 
- For video, conditioning on a person bounding box sequence, we predict the body joint locations in the current frame or, for the task of body pose forecasting, at a specific point in the future.
- In the mocap case, the input and output domains coincide (3D body joint angles).
- In the video case, the input and output domains differ (raw video pixels versus body joint locations).



### Dataset 

- **Human3.6M**: Subject **[5]** for testing, train with the rest.



### Metric result

- Comparison
    - Multilayer LSTM models (No previous works on motion prediction).
    - Video pose labeling:
        - Perframe body part CNN detector. 
    - Future pose forecasting:
        - First order motion modeling with optical flow constancy assumptions. 
        