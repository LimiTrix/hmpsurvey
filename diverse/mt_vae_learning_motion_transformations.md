# MT-VAE: Learning Motion Transformations
> ### Xinchen Yan, Akash Rastogi, Ruben Villegas, Kalyan Sunkavalli, Eli Shechtman, Sunil Hadap, Ersin Yumer, Honglak Lee

| ![Network](/assets/mt_vae_models.png) | 
| :--: |
| __MT-VAE Network Diagram__ |

| ![Paradigm](/assets/mt_vae_paradigm.png) |
| :--: |
| __Training Paradigm__ |



<!-- ### Architecture

-  -->



## Challenge & Motivation
 
- Claims that modeling the dynamics of human body is a fundamental problem in computer vision, graphics, and machine intelligence. It has a broad range of applications ranging from virtual characters, video-based animation and editing, and human-robot interfaces. 
- Claims that human motion is a highly structured and can be modeled as a sequence of atomic units known as _motion modes_. 
    - Motion mode captures the _short-term_ temporal dynamics of a human action (e.g., smiling/walking), including its stylistic attributes (e.g., how wide the smile, how fast the walk).
    - Long term motion can be segmented into a series of motion modes with transition in between them (e.g., transition between smiling to laughing). 



## Solution

- They hypothesize that:
    - Motion mode can be represented as a low-dimensional feature vector. 
    - Transition between motion modes can be modeled as transformations of these features. 
- Proposed a novel model _Motion Transformation Variational Auto-Encoders (MT-VAE)_ for learning sequence generation.
    - Implemented using LSTM encoder-decoder that embeds each short sub-sequence into a feature vector that can be decoded to reconstruct the motion. 
    - This method depends heavily on the theory that the transition between current modes (sequence) and future modes can be captured by a certain transformation.
- Understands that human motion is inherently multimodal.
    - A deterministic model is incapable of learning the motion variation and may collapse to a single-mode distribution.
    - Claims that their proposed method supports stochastic sampling of the feature hence is capable of generating a multiple plausible motion from a single input.



## Result

- Dataset: __Human3.6m__
- Tested on 2 different subjects:
    - Human Motion Prediction.
    - Analogy-based motion transfer (facial expression)

        