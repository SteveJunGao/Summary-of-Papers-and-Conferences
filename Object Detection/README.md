## YOLO [[PDF]](https://arxiv.org/abs/1506.02640)
- Treat the classificaiton as regression problem, regress the BoundingBox coordinates, IOU confidence and class probabilities.
- Unified detection pipeline, divide the image into S*S grids and each grid is only responsible for one object. (different bbxs may improve accuracy?)
- Training target allocation, allocated the target to the maximum IOU prediction, which will encourage the bbx predictor do better and will not surpress the false bbx.
- Only 7*7*2 objects' bbxs in the final output, some large may be recognized by several bbxs, we do Non-Maximal Suppression.
- Liminitatoin: Each grid might output several bbxs but the same class, struggles at multi small objects.
- Looking at the loss function, you could get more insights.
  ![Loss Function](YOLO_Loss_Function.png)

------------------------------

## SSD [[PDF]](https://arxiv.org/abs/1512.02325)
- High level idea: Multi scale feature map compared with Faster RCNN which only use the final layer as the feature map. Using features from lower layer to produce detection results and NMS to reduce the bbxs.
- Each layer output $mnk(C+4)$ values with m*n means faature map's size, k is the number of relative bbx and C is the classes number.
- Matching Strategy: boxes whoes IOU exceed some threshold (0.5) relative to the ground truth and boxes who has the maximum IOU with the grounf truth. (Mose Essential)


------------------------------

## YOLO9000 [[PDF]](https://arxiv.org/abs/1612.08242)
- 9000 means 9000 class labels.
- Better: Batch Normalization, High Resolution, Multi-scale training
- **Anchor Boxes**: before training, to gain the priors of anchors, the author puts all the ground truth boxes (in all data) to the same images, and run clustering algorithms to gain the anchor's priors
- Use MSCOCO to train object detector (bounding box regression) and ImageNet to train the classification
- Hierarchical classification tree to handle 9000 classes
- One thinking: Why the bounding box regressor could find the boundingbox of objects that do not apprear in the MSCOCO dataset and only appears at the ImageNet?
  It might because of the of the bbox regressor is only respoinsible for the object and not dependent to some object class label.

-----------------------------
## Feature Pyramid Network for Object Detection [[PDF]](https://arxiv.org/abs/1612.03144)
- Something like U-Net an Seg-Net

-----------------------------
## A-Fast-RCNN, Hard Positive Generation via Adversary for Object Detection [[PDF]](https://arxiv.org/abs/1704.03414)
- Something like a learnable Dropout.
- Adversarial dropout

-----------------------------
## Straight to Shapes: Real-time Detection of Encoded Shapes [[PDF]](http://www.robots.ox.ac.uk/~tvg/publications/2017/straightToShapes.pdf)
- While doing object detection, we are also interested in the shape of these objects.
- Before training the detection network, the author pretrain a **Shape Embedding** AutoEncoder to get the embedding of different shape, and use these embedding vector as the ground truth of the predicted shape.

-----------------------------
## Mask RCNN [[PDF]](https://arxiv.org/abs/1703.06870)
- Parrallel fully convolutional branch for mask prediction, different classes have their own mask prediction layer.
- **ROIAlign** layer to mitigate misalignments between RoI and the extracted features.

---------------------

## Learning Non-Maximum Suppression [[PDF]](https://arxiv.org/abs/1705.02950)

- A learnable Non-maximum suppression.
- Input is the detection output (confidence score and axis coordinates). 
- Each Block (Gossip Net) is used to concatenate the information from nearing bounding boxes, this is something like Graph CNN,  each bounding box could be treated as a node at the graph and if two bbox is close to each other (IOU is larger than *t* ), then we add an edge to connect these two nodes