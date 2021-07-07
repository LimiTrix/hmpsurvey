# Structural-RNN: Deep Learning on Spatio-Temporal Graphs
> ### Ashesh Jain, Amir R. Zamir, Silvio Savarese, Ashutosh Saxena
![Network](/assets/structural_rnn_models.png)



### Architecture

- __Left image__: Previous 
    - Feeds the GT as input while training.
    - Uses LSTM.
- __Right image__: GRU_Martinez:
    - No spatial encoding layer. 
    - Uses GRU instead of LSTM.
    - Feeds the prediction result instead of GT while training.



## Challenge

- They claim that bringing spatio-temporal structures and rich sequence modeling capabilities together is of particular importance for many applications. 
- Also claims that RNN lacks a high-level and intuitive spatio-temporal structure.



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
    - We borrow ideas from research on the statistics of hand motion [15], and model velocities instead of absolute joint angles, while keeping the loss in the original angle representation to avoid drift. Therefore, we propose a residual architecture that models first-order motion derivatives, which results in smooth and much more accurate short-term predictions.
    - Used GRU instead of LSTM and does not have spatial encoding layer.
    - Trained on whole H36M dataset instead of specific category. 



### Dataset 

- **Human3.6M**: Subject **[5]** for testing, train with the rest.



### Metric result

- Comparison
    - 