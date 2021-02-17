# :fire: PNG Upscale -  AI Super Resolution :fire:
> Because Bicubic Interpolation isn't good enough anymore, we are in the Machine Learning Age.
 
 ## [v1.0 is available on MediaFire due to large size](http://www.mediafire.com/file/xbwpmc4f3ztkql4/PNG_Upscale_v1.0.zip/file) 
* RAR include full "Models" folder 📁 and executable Jar 🖼️ 
* The Models folder needs to be in the same directory as the Jar to use them
* This program is best used on PNG images
* ⚠️ Be careful when trying to upsize large pictures, it will take time and resources ⚠️
* To upscale an image you just need to choose a mode, load a picture and press start
* Save button can be used to choose an output folder *before* you start the process 



## Models

There are four trained models integrated into the program

#### EDSR

> Trained models can be downloaded from [here](https://github.com/Saafke/EDSR_Tensorflow/tree/master/models).

- Size of the model: ~38.5MB. This is a quantized version, so that it can be uploaded to GitHub. (Original was 150MB.)
- This model was trained for 3 days with a batch size of 16
- Link to implementation code: https://github.com/Saafke/EDSR_Tensorflow
- x2, x3, x4 trained models available
- Advantage: Highly accurate
- Disadvantage: Slow and large filesize
- Speed: < 3 sec for every scaling factor on 256x256 images on an Intel i7-9700K CPU.
- Original paper: [Enhanced Deep Residual Networks for Single Image Super-Resolution](https://arxiv.org/pdf/1707.02921.pdf) [1]

#### ESPCN

> Trained models can be downloaded from [here](https://github.com/fannymonori/TF-ESPCN/tree/master/export).

- Size of the model: ~100kb
- This model was trained for ~100 iterations with a batch size of 32
- Link to implementation code: https://github.com/fannymonori/TF-ESPCN
- x2, x3, x4 trained models available
- Advantage: It is tiny and fast, and still performs well.
- Disadvantage: Perform worse visually than newer, more robust models.
- Speed: < 0.01 sec for every scaling factor on 256x256 images on an Intel i7-9700K CPU.
- Original paper: [Real-Time Single Image and Video Super-Resolution Using an Efficient Sub-Pixel Convolutional Neural Network](https://arxiv.org/pdf/1707.02921.pdf) [2]

#### FSRCNN

> Trained models can be downloaded from [here](https://github.com/Saafke/FSRCNN_Tensorflow/tree/master/models).

- Size of the model: ~40KB (~9kb for FSRCNN-small)
- This model was trained for ~30 iterations with a batch size of 1
- Link to implementation code: https://github.com/Saafke/FSRCNN_Tensorflow
- Advantage: Fast, small and accurate
- Disadvantage: Not state-of-the-art accuracy
- Speed: < 0.01 sec for every scaling factor on 256x256 images on an Intel i7-9700K CPU.
- Notes: FSRCNN-small has fewer parameters, thus less accurate but faster.
- Original paper: [Accelerating the Super-Resolution Convolutional Neural Network](http://mmlab.ie.cuhk.edu.hk/projects/FSRCNN.html) [3]

#### LapSRN

Trained models can be downloaded from [here](https://github.com/fannymonori/TF-LapSRN/tree/master/export).

- Size of the model: between 1-5Mb
- This model was trained for ~50 iterations with a batch size of 32
- Link to implementation code: https://github.com/fannymonori/TF-LAPSRN
- x2, x4, x8 trained models available
- Advantage: The model can do multi-scale super-resolution with one forward pass. It can now support 2x, 4x, 8x, and [2x, 4x] and [2x, 4x, 8x] super-resolution.
- Disadvantage: It is slower than ESPCN and FSRCNN, and the accuracy is worse than EDSR.
- Speed: < 0.1 sec for every scaling factor on 256x256 images on an Intel i7-9700K CPU.
- Original paper: [Deep laplacian pyramid networks for fast and accurate super-resolution](https://arxiv.org/pdf/1707.02921.pdf) [4]

### Benchmarks

Comparing different algorithms. Scale x4 on monarch.png

|               | Inference time in seconds (CPU)| PSNR | SSIM |
| ------------- |:-------------------:| ---------:|--------:|
| ESPCN            |0.01159   | 26.5471 | 0.88116 |
| EDSR             |3.26758     |**29.2404**  |**0.92112**  |
| FSRCNN           | 0.01298   | 26.5646 | 0.88064 |
| LapSRN           |0.28257    |26.7330   |0.88622  |
| Bicubic          |0.00031 |26.0635  |0.87537  |
| Nearest neighbor |**0.00014** |23.5628  |0.81741  |
| Lanczos          |0.00101  |25.9115  |0.87057  |

 ---
 
### As a Demo this image was resized from 256x256 to 85x85, and then upscaled using this program

![Original](https://github.com/Araxeus/PNG-Upscale/blob/main/test/original.png)


## x2 demo (85x85 > 170x170)

|      Original             |  Bicubic Interpolation    |        EDSR               |
| ------------------------- |------------------------- |------------------------- |
![Original](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/original.png)   |  ![Bicubic](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/input(BicubicX2).png) |  ![EDSR](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/input(EDSRx2).png) |

|         ESPCN             |       FSRCNN              |        LapSRN             |
| ------------------------- | ------------------------- | ------------------------- |
![ESPCN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/input(ESPCNx2).png) | ![FSRCNN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/input(FSRCNNx2).png) |  ![LapSRN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x2/input(LapSRNx2).png) |

> Bicubic Interpolation is the standart resizing technique used by most editing tools like photoship etc..


## x4 demo (85x85 > 340x340)

|      Original             |  Bicubic Interpolation    |        EDSR               |
| ------------------------- | ------------------------- | ------------------------- |
![Original](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/original.png)   |  ![Bicubic](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/input(BicubicX4).png)|  ![EDSR](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/input(EDSRx4).png)|

 
|        ESPCN             |       FSRCNN              |        LapSRN             |
| ------------------------- | ------------------------- | ------------------------- |
![ESPCN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/input(ESPCNx4).png)   |  ![FSRCNN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/input(FSRCNNx4).png)|  ![LapSRN](https://github.com/Araxeus/PNG-Upscale/blob/main/test/x4/input(LapSRNx4).png)|

### References
[1] Bee Lim, Sanghyun Son, Heewon Kim, Seungjun Nah, and Kyoung Mu Lee, **"Enhanced Deep Residual Networks for Single Image Super-Resolution"**, <i> 2nd NTIRE: New Trends in Image Restoration and Enhancement workshop and challenge on image super-resolution in conjunction with **CVPR 2017**. </i> [[PDF](http://openaccess.thecvf.com/content_cvpr_2017_workshops/w12/papers/Lim_Enhanced_Deep_Residual_CVPR_2017_paper.pdf)] [[arXiv](https://arxiv.org/abs/1707.02921)] [[Slide](https://cv.snu.ac.kr/research/EDSR/Presentation_v3(release).pptx)]

[2] Shi, W., Caballero, J., Huszár, F., Totz, J., Aitken, A., Bishop, R., Rueckert, D. and Wang, Z., **"Real-Time Single Image and Video Super-Resolution Using an Efficient Sub-Pixel Convolutional Neural Network"**, <i>Proceedings of the IEEE conference on computer vision and pattern recognition</i> **CVPR 2016**. [[PDF](http://openaccess.thecvf.com/content_cvpr_2016/papers/Shi_Real-Time_Single_Image_CVPR_2016_paper.pdf)] [[arXiv](https://arxiv.org/abs/1609.05158)]

[3] Chao Dong, Chen Change Loy, Xiaoou Tang. **"Accelerating the Super-Resolution Convolutional Neural Network"**, <i> in Proceedings of European Conference on Computer Vision </i>**ECCV 2016**. [[PDF](http://personal.ie.cuhk.edu.hk/~ccloy/files/eccv_2016_accelerating.pdf)]
[[arXiv](https://arxiv.org/abs/1608.00367)] [[Project Page](http://mmlab.ie.cuhk.edu.hk/projects/FSRCNN.html)]

[4] Lai, W. S., Huang, J. B., Ahuja, N., and Yang, M. H., **"Deep laplacian pyramid networks for fast and accurate super-resolution"**, <i> In Proceedings of the IEEE conference on computer vision and pattern recognition </i>**CVPR 2017**. [[PDF](http://openaccess.thecvf.com/content_cvpr_2017/papers/Lai_Deep_Laplacian_Pyramid_CVPR_2017_paper.pdf)] [[arXiv](https://arxiv.org/abs/1710.01992)] [[Project Page](http://vllab.ucmerced.edu/wlai24/LapSRN/)]

