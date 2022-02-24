# Self-Correction-Human-Parsing-on-Binary-Images


- [x] train.py
- [x] dataset.ipynb
- [x] dataset_and_train.ipynb
- [x] simple_extractor.py(inference)
- [x] requirements.txt

#

### Dataset

Dataset name: bodies-at-rest

Github repository: https://github.com/Healthcare-Robotics/bodies-at-rest

We used real dataset: 20 human participants (10M/10F) with 1K labeled real pressure images.

For prepairing binary images dataset, you can clone this repositiry and run `dataset.ipynb` file.


### Instalation

1- Clone this repository using the following command:

```
https://github.com/NahidEbrahimian/Self-Correction-Human-Parsing-on-Binary-Images
```

2- In ```./Self-Correction-Human-Parsing-on-Binary-Images``` directory, run the following command to install requirements:

```
pip install -r requirements.txt
```

#

### Train

1- Clone this repository using the following command:

```
https://github.com/NahidEbrahimian/Self-Correction-Human-Parsing-on-Binary-Images
```

There are two solutions for training:

1- You can run `dataset_and_train.ipynb` file for both prepairing dataset and training

2- Afther prepairing dataset, run the following command:

```
%cd ./Self-Correction-Human-Parsing-on-Binary-Images
!python train.py --data-dir ./dataset/dataset --num-classes 7 --batch-size 3 --imagenet-pretrain ./pretrain_model/resnet101-imagenet.pth
```

### Inference

1- For inference, first download pretrained model from this link and put in `./log` directory: [download model](https://drive.google.com/file/d/1-MGJP3ffp1OYEyirMx-l-uJ51k4Jlus9/view?usp=sharing)

2- Put your binary images in `./input` directory

3- Run the following command:

```
!python simple_extractor.py --dataset 'pascal' --model-restore "./log/checkpoint_40.pth.tar" --input-dir './input' --output-dir './output'
```


