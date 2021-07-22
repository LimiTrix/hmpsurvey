# On Human Motion Prediction using Recurrent Neural Network
> ### Julieta Martinez, Michael J. Black, Javier Romero
![Network](/assets/gru_martinez_network.png)



### Architecture

- __Left image__: Previous methods:
    - Have spatial encoding layer.
    - Feeds the GT as input while training.
    - Uses LSTM.
- __Right image__: GRU_Martinez:
    - No spatial encoding layer. 
    - Uses GRU instead of LSTM.
    - Feeds the prediction result instead of GT while training.



## Challenge

- "Handing over an object to another person, playing sports, or simply walking in a crowded street would be extremely 
challenging tasks without our understanding of how people move, and our ability to predict what 
they are likely to do in the following instants"
- "Since human motion is the result of both physical limitation and intentions of subjects, motion
modeling is a complext task that should be ideally learned from observations."
- Human motion prediction has received interest from a wide variety of fields:
    - Action prediction for socially aware robotics.
    - 3D people tracking within computer vision.
    - Motion generation for computer graphics.
    - Modeling biological motion in psychology.
- They __argue__ that:
    - Results from recent works are not fully satisfactory for either of these problems
    - Trying to address both problem (validation method) is very challenging when they don't have proper quantitative
    evaluation for long-term plausibility.



## Previous Works
- Compared to pose recognition networks.
- __ERD__ = Uses curriculum learning and incorporates representation learning in the architecture.
- __Structural-RNN__ = manually encodes the semantic similarity between different body parts. 
- Both above approaches benefit from large, publicly available collections of motion capture data.
and the recent advances in the optimization of time-series modeling (Autoencoder + RNNs)
- Validation technique for previous works:
    - Quantitative prediction error in the short-term, typically measured as a mean-squared loss
    in angle-space
    - Qualitative motion synthesis for longer time horizons. 
- They observed that latest deep-RNN based methods have difficulty obtaining good performance on both validation tasks. Those algorithms are trained to minimize a quantitative loss for short-term prediction while they tweak the architectures or learning procedures for long-term prediction.
- As a result, long-term suffer from unrealistic artifacts (foot sliding), and short-term results are bad cuz of clear 
discontinuities in the first prediction. 



## Solution

- Focus on short-term prediction (claimed to be the most relevant task for visual tracking).
- Tried to investigate the reason behind poor performance by:
    - Analyzing network architectures and training procedures used in SOTA RNN methods.
- __ERD & Structural RNN__ both fed only the GT data during training. This is a known mistake for RNN and reinforcement learning as the networks won't be able to learn from their mistakes.
- To compensate the above's effect, they introduce random noise during training. However the noise is challenging to tune, which in turn makes it challenging to decide the best network based on validation error and has the effect of degrading the
quality of prediction in the first frame prediction.
- __Proposal__:
    - "Simple approach" = feed the prediction result, just like in test time, instead of ground truth while training.
    They claim this increases the robustness of the prediction compared to a network trained only on GT
    - We borrow ideas from research on the statistics of hand motion [15], and model velocities instead of absolute joint angles, while keeping the loss in the original angle representation to avoid drift. Therefore, we propose a residual architecture that models first-order motion derivatives, which results in smooth and much more accurate short-term predictions.
    - Used GRU instead of LSTM and does not have spatial encoding layer.
    - Trained on whole H36M dataset instead of specific category. 



### Dataset 

- **Human3.6M**: Subject **[5]** for testing, train with the rest.



### Code Validation
| Walking | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.28  | 0.49 |  0.72 |  0.81 |
| Retrain Result | 0.262 | 0.458 | 0.685 | 0.769 |

| Eating | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.23 |0.39| 0.62 | 0.76 |
| Retrain Result | 0.235 | 0.400 | 0.649 | 0.806 |

| Smoking | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.33 | 0.61 |1.05 |1.15 |
| Retrain Result | 0.318 | 0.590 | 1.001 | 1.095 |

| Discussion | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.31 |0.68| 1.01| 1.09
| Retrain Result | 0.302 | 0.678 | 1.007 | 1.093 | 

| Directions | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.26 |0.47| 0.72| 0.84
| Retrain Result | 0.416 | 0.660 | 0.828 | 0.943 |

| Greeting | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.75| 1.17| 1.74| 1.83
| Retrain Result | 0.509 | 0.848 | 1.292 | 1.472 |

| Phoning | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.23| 0.43| 0.69| 0.82
| Retrain Result | 0.592 | 1.094 | 1.493 | 1.648 |

| Posing | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.36| 0.71| 1.22| 1.48
| Retrain Result | 0.541 | 0.957 | 1.531 | 1.799 |

| Purchases | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.51| 0.97| 1.07| 1.16
| Retrain Result | 0.584 | 0.803 | 1.115 | 1.182 |

| Sitting | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.41| 1.05| 1.49| 1.63
| Retrain Result | 0.436 | 0.722 | 1.189 | 1.409 |

| Sitting Down | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.39| 0.81| 1.40| 1.62
| Retrain Result | 0.465 | 0.878 | 1.370 | 1.574 |

| Taking Photo | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.24 |0.51| 0.90| 1.05
| Retrain Result | 0.297 | 0.577 | 0.914 | 1.050 |

| Waiting | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.28| 0.53| 1.02| 1.14 
| Retrain Result | 0.335 | 0.661 | 1.137 | 1.320 |

| Walking Dog | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.56 |0.91| 1.26| 1.40
| Retrain Result | 0.539 | 0.907 | 1.251 | 1.379 |

| Walking Together | 80 | 160 | 320 | 400 |
| :--: | :--: | :--: | :--: | :--: |
| Paper's Result | 0.31| 0.58| 0.87| 0.91
| Retrain Result | 0.261 | 0.534 | 0.757 | 0.797 |