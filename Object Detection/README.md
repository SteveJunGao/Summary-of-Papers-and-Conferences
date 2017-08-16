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
- Berrer: Batch Normalization, High Resolution, Multi-scale training
- Anchor Boxes: before training, to gain the priors of anchores, the author puts all the ground truth boxes (in all data) to the same images, and run clustering algorithms to gain the anchor's priors
- Use MSCOCO to train object detector (bounding box regression) and ImageNet to train the classification
- Hierarchical classfication tree to handle 9000 classes
- One thinking: Why the bounding box regressor could find the boundingbox of objects that do not apprear in the MSCOCO dataset and only appears at the ImageNet?
It might because of the of the bbox regressor is only respoinsible for the object and not dependent to some object class label.

-----------------------------
## Feature Pyramid Network for Object Detection [[PDF]](https://arxiv.org/abs/1612.03144)
- Something like U-Net an Seg-Net

-----------------------------
## A-Fast-RCNN, Hard Positive Generation via Adversary for Object Detection [[PDF]](https://arxiv.org/abs/1704.03414)
- Something like a learnable Dropout.
- Adversarial dropout