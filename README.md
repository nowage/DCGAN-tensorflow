# celebA의 download path 오류 문제 임시 해결 버전임.
https://drive.google.com/drive/folders/0B7EVK8r0v71pTUZsaXdaSnZBZzg 에서 파일 다운 받아 /home/u1/test/DCGAN-tensorflow/data/ 폴더에 넣고 실행할 것. (/home/u1/test/DCGAN-tensorflow/data/img_align_celeba.zip)


---------------------------------------
# DCGAN in Tensorflow

Tensorflow implementation of [Deep Convolutional Generative Adversarial Networks](http://arxiv.org/abs/1511.06434) which is a stabilize Generative Adversarial Networks. The referenced torch code can be found [here](https://github.com/soumith/dcgan.torch).

![alt tag](DCGAN.png)

* [Brandon Amos](http://bamos.github.io/) wrote an excellent [blog post](http://bamos.github.io/2016/08/09/deep-completion/) and [image completion code](https://github.com/bamos/dcgan-completion.tensorflow) based on this repo.
* *To avoid the fast convergence of D (discriminator) network, G (generator) network is updated twice for each D network update, which differs from original paper.*


## Online Demo

[<img src="https://raw.githubusercontent.com/carpedm20/blog/master/content/images/face.png">](http://carpedm20.github.io/faces/)

[link](http://carpedm20.github.io/faces/)


## Prerequisites

- Python 2.7 or Python 3.3+
- [Tensorflow 0.12.1](https://github.com/tensorflow/tensorflow/tree/r0.12)
- [SciPy](http://www.scipy.org/install.html)
- [pillow](https://github.com/python-pillow/Pillow)
- (Optional) [moviepy](https://github.com/Zulko/moviepy) (for visualization)
- (Optional) [Align&Cropped Images.zip](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) : Large-scale CelebFaces Dataset


## Usage

First, download dataset with:

    $ python download.py mnist
    $ python download.py celebA

To train a model with downloaded dataset:

    $ python main.py --dataset mnist --input_height=28 --output_height=28 --c_dim=1 --is_train
    $ python main.py --dataset celebA --input_height=108 --is_train --is_crop True

To test with an existing model:

    $ python main.py --dataset mnist --input_height=28 --output_height=28 --c_dim=1
    $ python main.py --dataset celebA --input_height=108 --is_crop True

Or, you can use your own dataset (without central crop) by:

    $ mkdir data/DATASET_NAME
    ... add images to data/DATASET_NAME ...
    $ python main.py --dataset DATASET_NAME --is_train
    $ python main.py --dataset DATASET_NAME
    $ # example
    $ python main.py --dataset=eyes --input_fname_pattern="*_cropped.png" --c_dim=1 --is_train

## Results

![result](assets/training.gif)

### celebA

After 6th epoch:

![result3](assets/result_16_01_04_.png)

After 10th epoch:

![result4](assets/test_2016-01-27 15:08:54.png)

### Asian face dataset

![custom_result1](web/img/change5.png)

![custom_result1](web/img/change2.png)

![custom_result2](web/img/change4.png)

### MNIST

MNIST codes are written by [@PhoenixDai](https://github.com/PhoenixDai).

![mnist_result1](assets/mnist1.png)

![mnist_result2](assets/mnist2.png)

![mnist_result3](assets/mnist3.png)

More results can be found [here](./assets/) and [here](./web/img/).


## Training details

Details of the loss of Discriminator and Generator (with custom dataset not celebA).

![d_loss](assets/d_loss.png)

![g_loss](assets/g_loss.png)

Details of the histogram of true and fake result of discriminator (with custom dataset not celebA).

![d_hist](assets/d_hist.png)

![d__hist](assets/d__hist.png)


## Author

Taehoon Kim / [@carpedm20](http://carpedm20.github.io/)
