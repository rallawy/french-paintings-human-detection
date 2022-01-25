# french-paintings-human-detection by Raya Allawy 
This repository detects humans in French paintings using the YoloV5 model and my own annotated dataset.
This project was done for the class Collecting Data with Professor Federico Pianzola (PhD). 

## About this project: 

Dataset for French Paintings was collected from the website Web Gallery of Art. Each image was then annotated to be put in a human detection machine. 
The purpose of this machine is to detect any humans in each painting and to disregard anything that is non-human. 

## Dataset:
I used the method of webscraping to get the images for the dataset from the website Web Gallery of Art images were filtered by French Paintings only.

The dataset was split into 80 percent train and 20 percent validation.

## Annotations:
The images were annotated using the website Roboflow.

For each human in the French paintings I drew a bounding box around them and generated a .txt file with the bounding boxes coordinates (class, center coordinates, width, height)

There were 1,500 plus images annotated but this is not enough to train a complex model like YOLOv5 so more data was needed and therfore augmentations were added to the images with the augmentation steps I was able to generate around 3 times more data than we had before. These augmentations inlcuded, rotation, horizontal flip, saturation, hue, brightness, and cutout. With these augmentations synthetic data was generated and I was able to use YOLOv5 to train.
