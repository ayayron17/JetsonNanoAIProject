# JetsonNanoAIProject
## My project goal is to recognize different types of trash whether to recycle or put it in the garbage.
## This project was run through Google Colab and VSCode using the pre-set NVIDIA Jetson Nano database.
---

## Step 1: Training the Model in Google Colab

## [Link to the project](https://colab.research.google.com/gist/Charlotteec/d625a314ed1ea177e632c210e06c8b28/train_model_backup.ipynb)

## I decided to use Google Colab because my Nano was too slow to train and it was taking up storage.

1.1: First 3 Commands

1. Run the command below to clone a repository to setup the base of the project.
   
```bash
git clone https://github.com/dusty-nv/pytorch-classification.git
ls
```
2. This command changes directories into the new file and installs libraries in order to run the project.
   
```bash
cd pytorch-classification
pip install -r requirements.txt
```

3. This command downloads a zip file with the name 'cat_dog.tar.gz' which contains all the training images for the project.

```bash
cd pytorch-classification/data
wget https://nvidia.box.com/shared/static/o577zd8yp3lmxf5zhm38svrbrv45am3y.gz -O cat_dog.tar.gz
tar xzf cat_dog.tar.gz
```

1.2: Gather a Dataset

I downloaded 7 datasets from images.cv (battery, cardboard, carton, glass, metal, paper, plastic)

Take your own pictures of any trash you wish to train or find datasets on the Internet.

I uploaded the datasets onto my Drive and imported the files into Google Colab.

1.3 Sort out the Dataset Files

Under pytorch-classification/data create a new folder called 'total_data'.

Within the new folder, create 3 new folders (test, train, val)

Through the imported Google Drive, drag folders containing the images you downloaded for the dataset.

Have most images go to train, some to val and the least to test.

1.4 Train the Model

Run this command but replace both 'cat_dog' with 'total_data'

This command will train the model and automatically stop at 34 epochs.

```bash
cd pytorch-classification
python3 train.py -b 30 --model-dir=models/cat_dog data/cat_dog
```

to:

```bash
cd pytorch-classification
python3 train.py -b 30 --model-dir=models/total_data data/total_data
```
---

## Step 2: Convert the Model to ONNX File in VSCode

2.1: Download the Model from Google Colab

Navigate to pytorch-classification/models/total_data

Download the file named 'model_best.pth.tar'

2.2 Upload the Model to VSCode

Navigate to jetson-inference/python/training/classification/models

Create a new folder called 'final_model'

Upload the model 'model_best.pth.tar' into the folder 'final_model'

2.3 Convert the Model to ONNX File

Change directories into jetson-inference/python/training/classification with:

```bash
cd pytorch-classification/python/training/classification
```

Run the command below to convert the file:

```bash
python3 onnx_export.py --model-dir=models/final_model
```
---

## Step 3: Creating a labels.txt File

3.1 

## Step 3: Test the Model with Testing Images

3.1: Gather a Small Testing Dataset 

Take pictures of the objects of the datasets you want to test to the model.
