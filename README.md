# Pedestrian Intention Prediction (based on [MotionBert](https://github.com/Walter0807/MotionBERT))

## Introduction

This project propose a model to predict the intention of pedestrians in a video. The model is based on the [MotionBert](https://github.com/Walter0807/MotionBERT) model. The model is trained on the [JAAD dataset](https://data.nvision2.eecs.yorku.ca/JAAD_dataset/) and evaluated on the same dataset. For more information about the model and its performances, please refer to the <span style="color:red">Report.md</span> documentation.

This project was made in the context of the [CIVIL-459:Deep Learning for Autonomous Vehicles](https://edu.epfl.ch/coursebook/en/deep-learning-for-autonomous-vehicles-CIVIL-459) course at EPFL. The goal was to solve a task related to autonomous vehicles using deep learning, in groups of 2,that bring a contribution to the state of the art in order in the end to reproduce the autopilot of an autonomous vehicle.

## Installation

To install the project and be able to run it, you need to follow the following steps:

1. Clone the repository:
2. Install the requirements:

```bash
conda create -n mb_pip python=3.7 anaconda
conda activate mb_pip
# Please install PyTorch according to your CUDA version.
conda install pytorch torchvision torchaudio pytorch-cuda=11.6 -c pytorch -c nvidia
pip install -r requirements.txt
```

## Training

In this part we will explain how to train the model on the JAAD dataset.

1. Follow the procedure of the part <span style="color:red">Create Dataset for training</span> to create the dataset and put it in the `data` folder.
2. create a config file in the `config` folder. You can use the `config/JAAD_train.yaml` file as a template.
3. Fill the config file with the correct paths to the dataset and the correct wanted parameters.
4. Run the following command:

#### From scracth :
```bash
python tain.py --config config/<your_config_file>.yaml -f <print_frequency>
```
#### From a checkpoint :
```bash
python tain.py --config config/<your_config_file>.yaml -f <print_frequency> -c
```

### Visualize logs with Tensorboard

The code will automatically create a folder named `logs` in the root directory of the project. You can visualize the logs with Tensorboard by running the following command:

```bash
tensorboard --logdir=logs/
```

## Evaluation

In this part we will explain how to evaluate the model on the JAAD dataset.

1. Follow the procedure of the part <span style="color:red">Create Dataset for training</span> to create the dataset and put it in the `data` folder.
2. create a config file in the `config` folder. You can use the `config/JAAD_eval.yaml` file as a template.
3. Fill the config file with the correct paths to the dataset and the correct wanted parameters (make sure that it is the same config file as the one used for training the model you want to evaluate).
4. Run the following command:

```bash
python tain.py --config config/<your_config_file>.yaml -f <print_frequency> -e
```

## Inference

In this part we will explain how to use the model to predict the intention of pedestrians on a video.

1. Follow the procedure of the part <span style="color:red">Create Dataset for Inference</span> to create the dataset from the video you want to use and put it in the `data` folder.
2. Create a config file in the `config` folder. You can use the `config/inference.yaml` file as a template.
3. Fill the config file with the correct paths to the dataset and the correct wanted parameters (make sure that it is the same config file as the one used for training the model you want to use).
4. Run the following command:

```bash
python inference.py --config config/<your_config_file>.yaml
```