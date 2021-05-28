# Human Motion Prediction Survey 

List of all the papers that I will explain throughout the survey. Work in Progress!
<br>

### Table of Contents

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->
- [**Datasets**](#datasets)
- [**Literature and Codes**](#literature-and-codes)
	- [Survey Papers](#survey-papers)
	- [Regression Prediction](#regression-prediction)
	- [Diverse Prediction](#diverse-prediction)
	- [Context-Aware Prediction](#context-aware-prediction)
	- [Miscellaneous Human Representation](#miscellaneous-human-body)
    <!-- - [Miscellaneous Prediction Method](#miscellaneous-prediction-method) -->
- [**Benchmark and Evaluation Metric**](#benchmark-and-evaluation-metric)
- [**Others**](#others)
	<!-- /TOC -->
<br>

## **Datasets**
| Docs | Dataset | Website / Download | Description  |
| :-: | :-: | :-: | :- | 
| [:x:](dataset\human-3-6-m.md) | [Human3.6M](https://arxiv.org/pdf/2004.05214.pdf) | [Project Page](http://vision.imar.ro/human3.6m/description.php) | Includes: RGB Image  Video, depth maps, poses, scanned 3D surface mesh, <br> 3D rigged human model in real videos, silhouette mask, 2d bounding boxes|
| [:x:](dataset/cmu-mocap.md) |  CMU Mocap | [Project Page](http://mocap.cs.cmu.edu/) |  | | |
| [:x:](dataset\penn-action.md) | [Penn Action](https://openaccess.thecvf.com/content_iccv_2013/papers/Zhang_From_Actemes_to_2013_ICCV_paper.pdf) | [Project Page](http://dreamdragon.github.io/PennAction/) |  
| [:x:](dataset/insta-variety.md) | [InstaVariety](https://arxiv.org/pdf/1812.01601.pdf) | [Project Page](https://github.com/akanazawa/human_dynamics/blob/master/doc/insta_variety.md) | From the paper "_Learning 3D Human Dynamics from Video_" | 

<br>

## **Literature and Codes**
### Survey Papers
| Name | Journal | Year | Description  |
| :-- | :-: | :-: | :- | 
| [A Review on Deep Learning Techniques for Video Prediction](https://arxiv.org/pdf/2004.05214.pdf) | TPAMI | 2020 | Survey on <ins>video prediction in general</ins> |
| [A survey on motion prediction and risk assessment for intelligent vehicles](https://robomechjournal.springeropen.com/track/pdf/10.1186/s40648-014-0001-z.pdf) | Springer | 2014 | Survey on <ins>autonomous vehicle</ins> |
| [Human Motion Trajectory Prediction: A Survey](https://arxiv.org/pdf/1905.06113.pdf) | IJRR | 2019 | Survey on <ins>human trajectory prediction</ins> |

<br>

### Regression Prediction 
| Code | Docs | Name | Conference | Description | 
| :-: | :-: | :-- | :- | :-- |
| [:o:](https://gist.github.com/Seleucia/3a4f3fadc6a8dc215b4b6fd3d6c0b596)  | [:x:](regression/recurrent_network_models_for_human_dynamics.md) | [Recurrent Network Models for Human Dynamics](https://arxiv.org/pdf/1508.00271.pdf) | ICCV 2015 | Encoder > Recurrent > Decoder
| [:o:](https://github.com/una-dinosauria/human-motion-prediction) | [:x:](regression/deep_representation_learning_for_human_motion_prediction_and_classification.md)  | [Deep representation learning for human motion prediction and classification](https://arxiv.org/pdf/1702.07486.pdf) | CVPR 2016 | 
| [:o:](https://github.com/papagina/Auto_Conditioned_RNN_motion) | [:x:](regression/auto_conditioned_recurrent_networks_for_extended_complex_human_motion_synthesis.md) | [AUTO-CONDITIONED RECURRENT NETWORKS FOR EXTENDED COMPLEX HUMAN MOTION SYNTHESIS](https://openreview.net/pdf?id=r11Q2SlRW) | ICLR 2018 | 
| [:o:](https://github.com/limaosen0/DMGNN) | [:x:](regression/dynamic_multiscale_graph_neural_networks_for_3_d_skeleton_based_human_motion_prediction.md) | [Dynamic Multiscale Graph Neural Networks for 3D Skeleton-Based Human Motion Prediction](https://arxiv.org/pdf/2003.08802.pdf) | CVPR 2020 | GCN based motion prediction |

<br>

### Diverse Prediction
| Code | Docs | Name | Conference Year | Description | 
| :-: | :-: | :-- | :-: | :-- |
| [:o:](https://github.com/Khrylx/DLow) | [:x:](diverse/d_low_diversifying_latent_flows_for_diverse_human_motion_prediction.md) | [DLow: Diversifying Latent Flows for Diverse Human Motion Prediction](https://www.ecva.net/papers/eccv_2020/papers_ECCV/papers/123540324.pdf) | ECCV 2020 | Basically a 2 step latent space. Like a latent space within a latent space | 
| [:o:](https://github.com/xcyan/eccv18_mtvae) | [:x:](diverse/mt_vae_learning_motion_transformations.md) | [MT-VAE: Learning Motion Transformations](https://arxiv.org/pdf/1808.04545.pdf) | ECCV 2018 | propose a motion transformation VAE to jointly learn the motion mode feature and transition between motion modes | 

<br>

### Context-Aware Prediction
| Code | Docs | Name | Conference | Year | Description | 
| :-: | :-: | :-- | :-: | :-: | :-- |
| :x: | [:x:](context-aware\context_aware_human_motion_prediction.md) | [Context-aware Human Motion Prediction](https://openaccess.thecvf.com/content_CVPR_2020/papers/Corona_Context-Aware_Human_Motion_Prediction_CVPR_2020_paper.pdf) | CVPR | 2020 | Multiple RNN, 2 stream of inputs (human motion prediction + object context understanding) <br> Said to use the hidden state of both the motion prediction and context prediction. <br> Further reading is necessary to untangle the mystery. | 
| [:o:](https://github.com/ZheC/GTA-IM-Dataset) | [:x:](context-aware/long_term_human_motion_prediction_with_scene_context.md) | [Long-term Human Motion Prediction with Scene Context](https://arxiv.org/pdf/2007.03672.pdf) | ECCV | 2020 | GoalNet > PathNet > PoseNet <br> GoalNet = CVAE: Predicts possible goals given image (sequence?) <br> PathNet = Hourglass54: Predicts paths + depth? to goal given goal from GoalNet <br> PoseNet = Transformer: Generate motion using 2d motion history (input) + path

<br>

### Miscellaneous Human Body

| Code | Docs |Body Type | Name | Conference Year | Description | 
| :-: | :-: | :-: | :-- | :-: | :-- |
| [:o:](https://github.com/akanazawa/human_dynamics) | [:x:](misc\predicting_3_d_human_dynamics_from_video.md) | SMPL |[Predicting 3D Human Dynamics from Video](https://arxiv.org/pdf/1908.04781.pdf#page=10&zoom=100,66,153) | ICCV 2019 | 3D body from image-sequence input. | 
| :x: | [:x:](misc\perpetual_motion_generating_unbounded_human_motion.md) | SMPL | [Perpetual Motion: Generating Unbounded Human Motion](https://arxiv.org/pdf/2007.13886.pdf) | CVPR 2020 | using SMPL param for body 
| :x: | [:x:](misc/we-are-more-than-our-joints-predicting-how-3-d-bodies-move.md) | Mocap 3D Keypoint | [We are More than Our Joints: Predicting how 3D Bodies Move](https://arxiv.org/pdf/2012.00619.pdf) | CVPR 2021 | Using sparseset of locations on the body surface that correspond to motion capture markers.
| [:o:](https://github.com/Khrylx/RFC) | [:x:](misc/residual-force-control-for-agile-human-behavior.md) | MuJoCo Simulated Skeleton| [Residual Force Control for Agile Human Behavior](https://proceedings.neurips.cc/paper/2020/file/f76a89f0cb91bc419542ce9fa43902dc-Paper.pdf) | NIPS 2020 | Using reinforcement learning to create motion synthesis
| :x: | [:x:](misc/3-d-motion-net-learning-continuous-flow-function-for-3-d-motion-prediction.md) | Human Scan | [3DMotion-Net: Learning Continuous Flow Function for 3D Motion Prediction](https://arxiv.org/pdf/2006.13906.pdf) | Arxiv | | Predicts over 3D human scan |

<br>

<!-- ### Miscellaneous Prediction Method -->

<!-- ### Benchmark and Evaluation Metrics -->

### Others
| Name | Conference | Year | Description  |
| :-- | :-: | :-: | :- | 
| [Learning and Recognizing Human Dynamics in Video Sequences](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=609382) | IEEE | 1997 | Show that interest in human dynamics model has emerged since 1997 | 
