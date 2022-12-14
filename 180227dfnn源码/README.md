# FusionNeuralNetwork about Person Re-ID using Pytorch

Reference codes:[baseline](https://github.com/layumi/Person_reID_baseline_pytorch)

## Prerequisites
- Python 3.6
- GPU 
- Pytorch 0.3+
- opecnv-python
- Numpy,Scipy,Matplotlib,and,so on.

## Model 
the deep fusion of NeuralNetwork--ResNet50 and hand-on feature LOMO,using FC to classify.

See as ./Model/...


## Install
- Install Pytorch from http://pytorch.org/
- Install Torchvision from the source
```
git clone https://github.com/pytorch/vision
cd vision
python setup.py install
```
## Dataset & Preparation
Download [Market1501 Dataset](http://www.liangzheng.org/Project/project_reid.html)

Preparation: Put the images with the same id in one folder. You may use 
```bash
python prepare.py
```
Remember to change the dataset path to your own path.

## Train

**Note: You Must Be Sure That There is A directory in FusionNeuralNetWork Called model Where must have the per-trained model about ResNet50.**
If not,come [here](https://github.com/layumi/Person_reID_baseline_pytorch) to train,using:
```bash
python train.py --gpu_ids 0 --name ft_ResNet50 --train_all --batchsize 32  --data_dir your_data_path --erasing_p 0.5
``` 
Also, we provide a ResNet50 Model which has been trained using Market1501.
You can download it from [here](https://pan.baidu.com/s/1w65fT80k0AVUafaYJS4tVQ).
if you already have it,just run:
```bash
python3 train.py --gpu_ids 0,1,2,3 --name LiangZiZuiShuai --read_name ft_ResNet50 --train_all --batchsize 2 --color_jitter --which_epoch last --FNN 
```
## Test
Use trained model to extract feature by
```bash
python test.py --gpu_ids 0 --name LiangZiZuiShuai --test_dir your_data_path  --which_epoch 59
```

## Evaluation
```bash
python evaluate.py
```


