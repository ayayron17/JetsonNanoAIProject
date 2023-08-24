# JetsonNanoAIProject
---

## Step 1: Training the Model in Google Colab

## [Link to the project](https://colab.research.google.com/gist/Charlotteec/d625a314ed1ea177e632c210e06c8b28/train_model_backup.ipynb)

1.1: First 3 Commands

```bash
git clone https://github.com/dusty-nv/pytorch-classification.git
ls
```
```bash
cd pytorch-classification
pip install -r requirements.txt
```
```bash
cd pytorch-classification/data
wget https://nvidia.box.com/shared/static/o577zd8yp3lmxf5zhm38svrbrv45am3y.gz -O cat_dog.tar.gz
tar xzf cat_dog.tar.gz
```
