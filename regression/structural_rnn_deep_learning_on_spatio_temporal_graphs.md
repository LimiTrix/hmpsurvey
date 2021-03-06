# Structural-RNN: Deep Learning on Spatio-Temporal Graphs
> ### Ashesh Jain, Amir R. Zamir, Silvio Savarese, Ashutosh Saxena
![Network](/assets/structural_rnn_models.png)



## Challenge

- They claim that bringing spatio-temporal structures and rich sequence modeling capabilities together is of particular importance for many applications. 
- Also claims that previous methods with RNN lacks a high-level and intuitive spatio-temporal structure.
- This paper is more catered to spatio-temporally related topics and is not specific to human motion prediction.



## Previous Works
- Some previous methods (including __Sristava _et al_.__ video prediction method) tried using RNN to solve a specific problem. 
Their network is designed only to solve a single specific problem.



## Solution

- Proposed a combination of Spatio-temporal network and recurrent networks:
    - Technical side is difficult to understand, but they are separating the relation on each object and connecting them 
    respectively.
    - Looking at the paper, unless I read it completely I don't think I will understand the network. At a glance, it is similar to a GCN where each node is a RNN.


### Dataset 

- **Human3.6M**: Subject **[5]** for testing, train with the rest.


<!-- 
### Metric result

- Comparison
    -  -->