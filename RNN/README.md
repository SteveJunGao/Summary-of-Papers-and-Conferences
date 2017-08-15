# NIPS-15 Schedualed Sampling for Sequence Prediction with RNN
- This paper provides a curriculum learning approach to mitigate the gap between the training and inference of sequence prediction of RNN. During training, we use the ground truth as input, but during inference, we sample from the output of pervious step. 
- We use \epsilon to represent the probability of selection of gound truth and 1-\epsilon the network's prediction, then we decay the \epsilon during training.
- Something I misunderstand the RNN is we only put the hidden layer of previous step to the current layer, but it also important to input the previous prediction result. (I can see this from the prediction result I get at present, for simple line curve(two points), the prediction is great, but for complicate curves(six points), the network performs worse)