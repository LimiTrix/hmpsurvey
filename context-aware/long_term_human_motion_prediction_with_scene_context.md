# Long-term Human Motion Prediction with Scene Context

GoalNet > PathNet > PoseNet
- GoalNet = CVAE: Predicts possible goals given image (sequence?)
- PathNet = Hourglass54: Predicts paths + depth? to goal given goal from GoalNet
- PoseNet = Transformer: Generate motion using 2d motion history (input) + path