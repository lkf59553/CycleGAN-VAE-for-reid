# Training CamStyle with CycleGAN and VAE for reid task

CamStyle is trained with [CycleGAN-pytorch](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix)

Replace VAE as a generator based on zhongzhun007's work [CamStyle](https://github.com/zhunzhong07/CamStyle)
### Preparation

#### Requirements: Python=3.6 and Pytorch=0.4.0

1. Install [Pytorch](http://pytorch.org/)

2. Download dataset
   
   - Market-1501   [[BaiduYun]](https://pan.baidu.com/s/1ntIi2Op) [[GoogleDriver]](https://drive.google.com/file/d/0B8-rUzbwVRk0c054eEozWG9COHM/view)
   
   - DukeMTMC-reID   [[BaiduYun]](https://pan.baidu.com/share/init?surl=kUD80xp) (password: chu1) [[GoogleDriver]](https://drive.google.com/file/d/0B0VOCNYh8HeRdnBPa2ZWaVBYSVk/view)
   
   - Move them to 'CamStyle/CycleGAN-for-CamStyle/datasets/market (or duke)'

# Train CamStyle models

  ```Shell
  # For Market-1501
  sh train_market.sh
  # For Duke
  sh train_duke.sh
  ```

# Generate CamStyle images

  ```Shell
  # For Market-1501
  sh test_market.sh
  # For Duke
  sh test_duke.sh
  ```
# Experiment result
Through FID (Frechet Inception Distance) and SSIM (Structural SIMilarity), two well-recognized indicators for evaluating image quality of GAN network , to campare the quality of images generated by Cycle-VAE-GAN and Cyle-GAN.
![Image text](https://github.com/xr-Yang/CycleGAN-VAE-for-reid/blob/master/distance_test/result.png)

- Cycle-VAE-GAN training takes less time. Replacing the ResnetGenerator in the original paper with the VAE encoder greatly reduced the number of convolution layers and improved training time.
- Regardless of the visual contrast or FID, SSIM and other image quality indicators can be reflected, Cycle-VAE-GAN has better image generation capabilities.
- Compared with the original paper, the accuracy is better on its baseline, both mAP and Rank-1 are improved.

## Conf
- Camera Style Adaptation for Person Re-identification
- Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networkss
- Image-to-Image Translation with Conditional Adversarial Networks
