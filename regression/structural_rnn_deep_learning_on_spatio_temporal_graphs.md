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
- Also claims that previous methods with RNN lacks a high-level and intuitive spatio-temporal structure.
- This paper is more catered to spatio-temporally related topics and is not specific to human motion prediction.



## Previous Works
- Some previous methods (including __Sristava _et al_.__ video prediction method) tried using RNN to solve a specific problem. 
Their network is designed only to solve a single specific problem.



## Solution

- Proposed a combination of Spatio-temporal network and recurrent networks:
    - 


### Dataset 

- **Human3.6M**: Subject **[5]** for testing, train with the rest.



### Metric result

- Comparison
    - 