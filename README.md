# Self-Correction-Human-Parsing-on-Binary-Images


|Original Images![original](https://user-images.githubusercontent.com/82975802/157465562-83906309-78f0-4390-a1b2-0d3e9a0321aa.jpg)|Contrast Enhancement![enhancment](https://user-images.githubusercontent.com/82975802/157465807-fda59e46-1c33-4e83-baf8-6a3499a8384e.jpg)|
| ------------- | ------------- |

|Output Pascal Model![pascal model](https://user-images.githubusercontent.com/82975802/157465918-2537f386-057c-4bc8-8cc5-0e1aeb5d5d44.png)|Binary Image-Input Model![input images](https://user-images.githubusercontent.com/82975802/157465975-637b2d44-27be-488b-9337-60d50f266539.jpg)|Inference Result![model inference](https://user-images.githubusercontent.com/82975802/157469098-9c593853-1104-42ce-a4ce-3315482fa9ee.png)|
| ------------- | ------------- | ------------- |

- [x] train.py
- [x] dataset.ipynb
- [x] dataset_and_train.ipynb
- [x] simple_extractor.py(inference)
- [x] requirements.txt
- [ ] evaluate.py

#

### Dataset

Dataset name: bodies-at-rest

Github repository: https://github.com/Healthcare-Robotics/bodies-at-rest

We used real dataset of bodies-at-rest dataset that contains 20 human participants (10M/10F) with 1K labeled real pressure images.

- prepairing binary images dataset:

For preparing dataset, we used pascal pretrained model that implemented for RGB images. The Pascal Person Part has 7 labels, including 'Background', 'Head', 'Torso', 'Upper Arms', 'Lower Arms', 'Upper Legs', 'Lower Legs'.

The steps for preparing the database are as follows

1- Extraction of image field of dataset pickle file 

2- Improve image contrast

3- Create segmented images using pascal model

4- Convert segmented images using pascal model to binary images

5- Creating labels of binary images that contains 7 classes

For prepairing binary images dataset, you can clone this repositiry and run `dataset.ipynb` file.

|step1 ![16](https://user-images.githubusercontent.com/82975802/158050748-421ab337-8498-4e90-bc96-aba5497ce9a6.jpg)|step2![16 (1)](https://user-images.githubusercontent.com/82975802/158050752-4b7358c3-ec59-431a-a1b9-ae5bed3f1dce.jpg)|step3![16 (1)](https://user-images.githubusercontent.com/82975802/158051013-db7548ff-9239-4b5b-b8af-af8863543ec8.png)|step4![16 (2)](https://user-images.githubusercontent.com/82975802/158051025-db2f45a8-3ab3-41d0-88ea-00920e278273.jpg)|step5![16](https://user-images.githubusercontent.com/82975802/158051028-d6fb91cd-5293-47b9-922b-3cee0420f8ad.png)|
| ------------- | ------------- | ------------- | ------------- | ------------- |

#

### Instalation

1- Clone this repository using the following command:

```
https://github.com/NahidEbrahimian/Human-Parsing-on-Binary-Images
```

2- In ```./Human-Parsing-on-Binary-Images``` directory, run the following command to install requirements:

```
pip install -r requirements.txt
```

#

### Train

1- Clone this repository using the following command:

```
https://github.com/NahidEbrahimian/Human-Parsing-on-Binary-Images
```

There are two solutions for training:

1- You can run `dataset_and_train.ipynb` file for both prepairing dataset and training

2- Afther prepairing dataset, run the following command:

```
%cd ./Human-Parsing-on-Binary-Images
!python train.py --data-dir ./dataset/dataset --num-classes 7 --batch-size 3 --imagenet-pretrain ./pretrain_model/resnet101-imagenet.pth
```

#

### Inference

1- For inference, first download pretrained model from this link and put in `./log` directory: [download model](https://drive.google.com/file/d/1-MGJP3ffp1OYEyirMx-l-uJ51k4Jlus9/view?usp=sharing)

2- Put your binary images in `./input` directory

3- Run the following command:

```
!python simple_extractor.py --dataset 'pascal' --model-restore "./log/checkpoint_40.pth.tar" --input-dir './input' --output-dir './output'
```


