# :framed_picture: Human Detection in French Paintings  :framed_picture: 
This repository detects humans in French paintings using the YoloV5 model and my own annotated dataset.
This project was done for the class Collecting Data with Professor Federico Pianzola (PhD). 

## About this project: 

This project is a new approach to detect humans in paintings using data augmentation and object detection machine learning models. To Describe a brief pipeline we can divide it in three steps: 

1. Collecting Data 
2. Data Annotation 
3. Augmentation 
4. Model Training and Testing 

## Dataset:
To collect the data I webscraped the website [Web Gallery of Art](https://www.wga.hu/) to get the images for the dataset. Images were filtered by French Paintings only. French paitnings were chosen because they represent more humans than other countries, which means we have enough data to train the model, I also have a BA in French language and literature which makes it easier to interpet the paintings.

[Click here](https://osf.io/twb32/) to acess my dataset in my OSF account. 

### Annotations:

For each human in the French paintings I drew a bounding box around them and generated a .txt file with the bounding boxes coordinates (class, center coordinates, width, height). This annotation file is in the YOLOv5 format and it can be interperted by the model. 

There were 1,500 plus images annotated (and resized to 640 by 640) but this is not enough to train a complex model like YOLOv5 so more data was needed and therfore augmentations were added to the images with the augmentation steps I was able to generate around 3 times more data than we had before. These augmentations inlcuded, rotation, horizontal flip, saturation, hue, brightness, and cutout. With these augmentations synthetic data was generated and I was able to use YOLOv5 to train.

To train the model I split the dataset into two different folders, training set (80%) and validation set (20%)

## Model: 
To start the detection [YOLOv5](https://arxiv.org/abs/1506.02640) (Redmon et al.) object detection model was used. The YOLO model processes images in real time at 45 fps. I used a smaller version of the network called YOLOv5s. YOLO learns very general representations of objects and it's ideal to be used as a human detection baseline.

To preform the training and the testing I used a machine learning framework called PyTorch and I used a pretrained version of [YOLOv5s](https://github.com/ultralytics/yolov5) which was trained on the COCO dataset.
I trained the model for 150 epochs using the early stopping technique (A technique where the model learns it's not detecting anything and it stops) 

## Experiments: 
![valentin_jpg rf 9063dfc225f51852425a824cbfd86c3a](https://user-images.githubusercontent.com/94530968/151046580-f34eb3fb-5944-4c23-ac40-7d6d3b761a86.jpg)

As you can see here this image was a result of testing the model. It detect two humans in the image. 

## Conclusion and Future works: 

The model needs some minor improvements. It has issues detecting smaller objects, perhaps this can be fixed by resizing the images to make them bigger (1080 by 1080 for example). Currently I was not able to taste this because of lack of computational power. 
