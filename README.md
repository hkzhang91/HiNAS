# HiNAS
Code for paper: 
> [Memory-Efficient Hierarchical Neural Architecture Search for Image Denoising (CVPR 2020)](https://arxiv.org/abs/1909.08228) 

> [Memory-Efficient Hierarchical Neural Architecture Search for Image Restoration](https://arxiv.org/abs/2012.13212)

Compared with the mehtod propsoed in Memory-Efficient Hierarchical Neural Architecture Search for Image Denoising, we made some improvements, which are explained in "log file for DNAS_For_IR"


## Requirements
```
This code is tested on Pytorch = 1.0.0.

I build my experimental environment by create a virtual env via anaconda3. 
After activating you env, you can install other all dependences via run: pip install -r requirements.txt. 
Note that,  to install graphviz, you also need to run: conda install graphviz. 
```

## Searching
```
#searching for denoising network
cd ./tools/
python search.py --config-file "../configs/dn/BSD500_3c4n/03_search_CR_R0.yaml" --device '0'

#searching for super-resolution network
cd ./tools/
python search.py --config-file "../configs/sr/DIV2K_3c3n/03_search_CR.yaml" --device '0'
```

## Training 
```
#training the founded denosing network with noise factor=30
cd ./tools/
python train.py --config-file "../configs/dn/BSD500_3c4n/03_train_CR_RO/train_s30.yaml" --device '0'

#training the founded super-resolution network with SR factor=3
cd ./tools/
python train.py --config-file "../configs/sr/DIV2K_2c3n/03_x3_train_CR.yaml" --device '0'
```
## Inference
```
# testing the trained denoising network with noise factor=[30 50 70]
cd ./tools/
python dn_eval.py --config-file "../configs/dn/BSD500_3c4n/03_train_CR_RO/03_infe.yaml" --device '0'

# testing the trained super-resolution network with sr factor=3
cd ./tools/
python sr_eval.py --config-file "../configs/sr/DIV2K_2c3n/03_x3_infe_CR.yaml" --device '0'
```

## Datasets
Fetch code:1111

>Denoising datasets: [BSD200](https://pan.baidu.com/s/1HS4g7DYUxZv-tqQNJI6WsA) [BSD300](https://pan.baidu.com/s/1WBGWtZj91p2x2bPRkmlWVw)

>Super-resolution datasets: [DIV2K_800](https://pan.baidu.com/s/1J6S0dTs1lJG3c0iqdQCBEA) [DIV2K_100](https://pan.baidu.com/s/1e6SrUTx94cWGSu0vjUXASA) [BSD100]() [BSDS100]() [Urban100]() [Manga109]() [General100]() [Set14]() [Set5]()



## Citation
If you use this code in your paper, please cite our papers
```
@inproceedings{zhang2020memory,
  title={Memory-efficient hierarchical neural architecture search for image denoising},
  author={Zhang, Haokui and Li, Ying and Chen, Hao and Shen, Chunhua},
  booktitle={Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition},
  pages={3657--3666},
  year={2020}
}
```
