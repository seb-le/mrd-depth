# MRD-Depth

This repository provides an official source code for:

> **Multi-Resolution Distillation for Self-Supervised Monocular Depth Estimation** </br>
> Pattern Recognition Letters, 2023

The code base is Monodepth2 (Godard et al. 2019).

## ⏳ Preparation for Training and Evaluation

**Please follow the several steps for training and evaluation.**


1> Download KITTI raw dataset and unzip it.
```shell
wget -i splits/kitti_archives_to_download.txt -P kitti_data/
cd kitti_data
unzip "*.zip"
cd ..
```
2> Convert the image format to png.
```shell
find kitti_data/ -name '*.png' | parallel 'convert -quality 92 -sampling-factor 2x2,1x1,1x1 {.}.png {.}.jpg && rm {}'
```
3> Download the [baseline model](https://github.com/brandleyzhou/DIFFNet) (Zhou et al. 2021) and locate them in `./checkpoints/diffnet` folder.

4> Extract ground-truth labels for evaluation
```shell
python export_gt_depth.py --data_path kitti_data --split eigen
```

## ⏳ Training & Evaluation

**Evaluate our model:**

You can evaluate the trained model as follows:
```shell
python evaluate_depth.py 
    --data_path [KITTI_DATA_ROOT]
    --eval_mono
```

## Pre-trained Weights

Comming Soon.


