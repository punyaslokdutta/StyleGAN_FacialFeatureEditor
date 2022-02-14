# StyleGan2-Colab-Demo
Notebook for training and generating samples with Colab and Google Drive using lucidrains' StyleGAN2 PyTorch implementation. The purpose of this demo is not to showcase high-resolution results - it is to demonstrate and explain the contributions of various techniques to perceptible result quality as well as the various problems that can be encountered when training GANs. As a result, many of the generated images in the demo are of noticeably poor quality (in various ways), because they are meant to be demonstrating modes of failure and/or the result of not incorporating certain techniques.

# Demo
The StyleGAN network has two features: generating high-resolution images using Progressive Growing, and incorporating image styles into each layer using AdaIN.
1. Progressive Growing GAN (generating high-resolution images)
2. AdaIN is a normalization method for style transfer  (StyleGAN)
3. The original StyleGAN Generator has a simple configuration. Without Progressive Growing, such simple generators has difficulty to generating high-resolution images a. But by increasing the expressive power of Generator and Discriminator, It seems possible to generate high resolution images without Progressive Growing.(StyleGan2 uses different method to produce high res + different Normalizatin method than ADAIn)
https://colab.research.google.com/drive/1uwPlY-4P_6fJ59SFRtgZLebVGgwGrUQu?usp=sharing

# GAN evaluation metrics
Because GAN is unsupervised learning, there are no established metrics like Accuracy or F1 score for supervised learning. Here, I introduce the frequently used metric called Frechet Inception Distance, and the Perceptual Path Length proposed by StyeGAN.

# Training Tool
training_small_set_demo.ipynb is a notebook used for training models with lucidrains' StyleGAN2 PyTorch implementation, using Colab
and Google Drive (because free compute is nice). Here is a link to the notebook on Colab:
https://colab.research.google.com/drive/1prEbP9AgZnxGCXtZkP-pgqRJoHcHJPou?usp=sharing

# Sample Images
Here is a link to the public directory on my Google Drive containing the generated sample images used in the
output_small_set_demo.ipynb notebook (equivalent to this repo's samples directory):
https://drive.google.com/drive/folders/1gpZKmuvOnsuRmCo3MEcpST_WC1Laaz3W?usp=sharing

# All Results
Here is a link to the public directory on my Google Drive containing all of the models and results from training using the
training_small_set_demo.ipynb notebook:
https://drive.google.com/drive/folders/1lBe6A5oTX6SuIg_iEoTcOdeC6-Quk9Ez?usp=sharing

# Project Progress
So far, this is a couple days' work and a few days of training, but I think it is already somewhat interesting. Expect updates whenever I have a few Colab GPUs to allocate to this (I am usually using all 4 for other projects). I should have some time for this mid-December, so I will try to get some results from: longer training on current configurations, training with lower network capacities (to deal with the pervasive mode collapse), some training on higher (512x512) resolution where applicable, and training current configurations with lower learning rates where useful (while demonstrating divergence due to high learning rate is useful (particularly for the afhq-dog model), there is value in showing the result on the same configuration with a tuned learning rate, however I don't intend to commit the time to tuning the learning rate for every model - these things take forever to train even with optimal learning rates).


