## Controllable facial attribute editing via Gaussian mixture model disentanglement
![teaser](example.png)
<p align="justify"><b>Figure 1:</b> Single attribute editing results compared with other methods.Each row represents the effect of editing in the opposite directions by differentmethods
</p>


> **Controllable facial attribute editing via Gaussian mixture model disentanglement**<br>
> BoLi<sup>a</sup>,Shu-HaiDeng<sup>a</sup>,BinLiu<sup>a</sup>,YikeLi<sup>a</sup>,Zhi-FenHe<sup>a</sup>,Yu-KunLai<sup>b</sup>,CongxuanZhang<sup>c</sup>,ZhenChen<sup>c</sup><br>
> https://www.sciencedirect.com/science/article/abs/pii/S1051200423000118
>
> <p align="justify"><b>Abstract:</b> <i>Generative adversarial networks (GANs) have made much progress in the field of high-quality and realistic facial image synthesis in recent years. However, compared with their powerful generation ability, it is difficult for users to modify the desired attributes of the resulting image while keeping the others. How to disentangle the latent space of pre-trained GANs is essential and critical for controllable image synthesis. In this paper, a novel controllable facial attribute editing algorithm based on the Gaussian mixture model (GMM) representation is proposed. First, we assume that the latent variables with respect to each facial attribute lie in a subspace of the whole latent manifold composed of a fixed number of learned features, and each attribute subspace can be modeled by a GMM. Then, to avoid unintended changes during attribute editing, a coordinate accumulation strategy with orthogonal regularization is introduced to enhance the independence of distinct attribute subspaces which helps improving the controllability of attribute editing. In addition, a resampling strategy is utilized to improve the stability of the model. Through qualitative and quantitative experimental results, the proposed method achieves the state-of-the-art performance on facial attribute editing, and improves the controllability of desired attribute editing.</i></p>


##Requirements
This code has been tested with Python 3.8, PyTorch 1.10, CUDA11.5, and GCC>=4.9 on Unbuntu 21.04. Install basic Machine Learning packages such as torchvision, PIL, etc.

## Usage
This repository includes versions of PGGAN and StyleGAN.

An example of face image editing using PGGAN:

####1. Petrained PGGAN models.
Download the [PGGAN weights](https://drive.google.com/file/d/1OgIp0ZEcUxnEWeNiUJF_PohMC84PWzN8/view?usp=share_link) pretrained on CelebA dataset and put the file to *checkpoints/*.
####2. Data prepared.
We have prepared vectors and their lables for training our model in [code_[0,1,2,5]_pggan.npy](https://drive.google.com/file/d/1wY40ESk-md47M4U94o9Cf_B0tvg2fnk_/view?usp=share_link) and [label_[0,1,2,5]_pggan.npy](https://drive.google.com/file/d/129B9Rp_OBBdOG721nly9PhdgAHXXItfK/view?usp=share_link) ,download and put them to *data/*, or you can prepare the training data yourself from *data/data_pre.py*
####3. Training command exmaple
   
```
   python GMM_PGGAN.py
   ```
the result models and direction vectors will be saved to *directions/* .
####4.  Test command exmaple
```
    python edit.py --models_dir /path to attribute vectors/
   ```
the editing results of one subject with linearly spaced attribute steps will be saved to *result/* . You may also use our pretrained [ latent directions](https://drive.google.com/file/d/1YYjsNqO3fVu15jJ1McXn1gix_28Zwrny/view?usp=share_link). 
  

If you want get the latent from special image,we also trained encoder for PGGAN model , you can get the latent code from *encode_pggan.py* . More pretrained models can be found [here](https://drive.google.com/drive/folders/1aNNQXIlFfm9RIvLliMmYc6fUXT6LwyRg?usp=sharing).

## Citation
If you find our work or repo useful in your research, please consider citing our paper:
```
@article{li2023controllable,
  title={Controllable facial attribute editing via Gaussian mixture model disentanglement},
  author={Li, Bo and Deng, Shu-Hai and Liu, Bin and Li, Yike and He, Zhi-Fen and Lai, Yu-Kun and Zhang, Congxuan and Chen, Zhen},
  journal={Digital Signal Processing},
  pages={103916},
  year={2023},
  publisher={Elsevier}
}
```
# CFAE
