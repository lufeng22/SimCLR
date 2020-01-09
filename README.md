# MVC
A PyTorch implementation of MVC based on the paper [Multi-View Combination for Unsupervised Visual Representation Learning]().

## Requirements
- [Anaconda](https://www.anaconda.com/download/)
- [PyTorch](https://pytorch.org)
```
conda install pytorch torchvision cudatoolkit=10.0 -c pytorch
```

## Dataset
`CIFAR10` dataset is used in this repo, the dataset will be downloaded by `PyTorch` automatically.

## Usage
### Train MVC
```
python train.py --epochs 50
optional arguments:
--model_type                  Backbone type [default value is 'resnet18'] (choices=['resnet18', 'resnet34', 'resnet50', 'resnext50_32x4d'])
--share_type                  Shared module type [default value is 'layer1'] (choices=['none', 'maxpool', 'layer1', 'layer2', 'layer3', 'layer4'])
--ensemble_size               Ensemble branch size [default value is 8]
--feature_dim                 Feature dim for each branch [default value is 16]
--negative_num                Negative sample number [default value is 4096]
--temperature                 Temperature used in softmax [default value is 0.1]
--momentum                    Momentum used for the update of memory bank [default value is 0.5]
--k                           Top k most similar images used to predict the label [default value is 200]
--batch_size                  Number of images in each mini-batch [default value is 128]
--epochs                      Number of sweeps over the dataset to train [default value is 200]
--with_random                 With branch random weight or not [default value is False]
--gpu_ids                     Selected gpu [default value is '0,1,2,3,4,5,6,7']
```

### Test MVC
```
python test.py --epochs 200 --batch_size 128
optional arguments:
--batch_size                  Number of images in each mini-batch [default value is 256]
--epochs                      Number of sweeps over the dataset to train [default value is 100]
--data_path                   Features extractor file [default value is 'epochs/cifar10_resnet18_layer1_32_4_features_extractor.pth']
--gpu_ids                     Selected gpu [default value is '0,1,2,3,4,5,6,7']
```

## Results

<table>
	<tbody>
		<!-- START TABLE -->
		<!-- TABLE HEADER -->
		<th>Name</th>
		<th>train time (s/iter)</th>
		<th>train mem (GB)</th>
		<th>Top1 Acc %</th>
		<th>Top5 Acc %</th>
		<th>download link</th>
		<!-- TABLE BODY -->
		<!-- ROW: r18 -->
		<tr>
			<td align="center">ResNet18</td>
			<td align="center">80.49</td>
			<td align="center">53.92</td>
			<td align="center">42.71</td>
			<td align="center">68.69</td>
			<td align="center"><a href="https://pan.baidu.com/s/1jP7zWezVPBZWx_9LjJCgWg">model</a>&nbsp;|&nbsp;xxi8</td>
		</tr>
		<!-- ROW: r50 -->
		<tr>
			<td align="center">ResNet50</td>
			<td align="center">81.16</td>
			<td align="center">54.54</td>
			<td align="center">43.61</td>
			<td align="center">69.50</td>
			<td align="center"><a href="https://pan.baidu.com/s/1BeGS7gckGAczd1euB55EFA">model</a>&nbsp;|&nbsp;1jhd</td>
		</tr>
	</tbody>
</table>

