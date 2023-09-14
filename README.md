# Detection of facial landmarks in thermal images using Computer Vision models
![image](https://media.tenor.com/9OCCAZolR_sAAAAC/thermal.gif)

## Overview
Thermal imaging stands as a remarkable and compact technique for detecting, quantifying, and displaying heat patterns, especially in situations where visible light is scarce. In healthcare sector,  thermal imaging is used to study a broad number of diseases where skin temperature can reflect the presence of inflammation in underlying tissues or where blood flow is increased or decreased due to a clinical irregularity. It can also be used to identify and analyze biosignal markers thereby helping with non-intrusive monitoring of body vital stats. The issue is today's readily available computer vision models have mostly been trained on visible light images due to whuch it would be difficult to just their performance with thermal images. In this project, I compare the performance of four pretrained computer vision models to identify facial landmarks.

## Dataset used
The  thermal images used in this project were sourced from [Université Laval Face Motion and Time-Lapse Video Database](http://www.qirt.org/liens/FMTV.htm) About 25 images of frontal and side profile views were chosen of mixed gender, some with presence or absence of facial hair and spectacles. Each model was then tested to detect facial landmarks (namely the face, nose and mouth).
<sub> Note: To access the thermal dataset please reach out to personnel mentioned on the [website](http://www.qirt.org/liens/FMTV.htm)</sub>

## Models used
Models | prerequisite xmls | Trained on | 
--- | --- | --- |
Haar Cascade| haarcascade_mcs_nose.xml, haarcascade_mcs_mouth.xml, haarcascade_frontalface_default.xml | frontal CALTECH dataset in 1999 |
DLib | shape_predictor_68_face_landmarks.dat | point iBUG 300-W dataset | 
Caffe | res10_300x300_ssd_iter_140000_fp16.caffemodel, deploy.prototxt |  [WIDER](http://shuoyang1213.me/WIDERFACE/) dataset which contains 32,203 public images and 393,703 labelled faces | 
MTCNN | - | [WIDER](http://shuoyang1213.me/WIDERFACE/) dataset which contains 32,203 public images and 393,703 labelled faces | 

## Results
<img align="center" alt="HC" width="600" height="600" src="https://github.com/SayanaVrgs/Detection_of_facial_landmarks_in_thermal_images_using_Computer_Vision_models/blob/main/haar%20cascade.png">
Although the face was identified in each image, the nose and mouth were not correctly identified and in some cases not identified at all
<img align="center" alt="DLIB" width="800" height="600" src="https://github.com/SayanaVrgs/Detection_of_facial_landmarks_in_thermal_images_using_Computer_Vision_models/blob/main/dlib.png">
In most of the images the facial landmarks were identified but in most side profiles and a few frontal images, the nose-mouth detections were incorrect
<img align="center" alt="CAFFE" width="800" height="600" src="https://github.com/SayanaVrgs/Detection_of_facial_landmarks_in_thermal_images_using_Computer_Vision_models/blob/main/Caffe.png">
Although not as good as Dlib, in quite a few images the facial landmarks were identified but in most side profiles and some frontal images, the nose-mouth detections were incorrect. In some images, facial landmarks were not identified at all.
<img align="center" alt="MTCNN" width="500" height="500" src="https://github.com/SayanaVrgs/Detection_of_facial_landmarks_in_thermal_images_using_Computer_Vision_models/blob/main/mtcnn.png">
This model was not great at detecting thermal images as it identified only 4 images to have facial landmarks. 

## Conclusion
A major reason why such well-known computer vision models failed was due to a lack of training data, more specifically, a lack of thermal image datasets. There are no readily available thermal images that can used to train the computer vision models. Hence thermal data collection is a major aspect that one must consider before embarking on training a computer vision model.
