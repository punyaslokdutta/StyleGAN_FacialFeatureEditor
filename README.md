# StyleGan2 Facial Features Editor
Notebook for training and generating samples with Colab and Google Drive using lucidrains' StyleGAN2 PyTorch implementation. The purpose of this demo is not to showcase high-resolution results - it is to demonstrate and explain the contributions of various techniques to perceptible result quality as well as the various problems that can be encountered when training GANs. As a result, many of the generated images in the demo are of noticeably poor quality (in various ways), because they are meant to be demonstrating modes of failure and/or the result of not incorporating certain techniques.

![illustartionCelebaHQ](https://user-images.githubusercontent.com/13198518/154096196-19525e20-fb5e-44e8-90a8-ab98aae6539e.jpeg)


# Demo
The StyleGAN network has two features: generating high-resolution images using Progressive Growing, and incorporating image styles into each layer using AdaIN.
1. Progressive Growing GAN (generating high-resolution images)
2. AdaIN is a normalization method for style transfer  (StyleGAN)
3. The original StyleGAN Generator has a simple configuration. Without Progressive Growing, such simple generators has difficulty to generating high-resolution images a. But by increasing the expressive power of Generator and Discriminator, It seems possible to generate high resolution images without Progressive Growing.(StyleGan2 uses different method to produce high res + different Normalizatin method than ADAIn)


# GAN evaluation metrics
Because GAN is unsupervised learning, there are no established metrics like Accuracy or F1 score for supervised learning. Here, I introduce the frequently used metric called Frechet Inception Distance, and the Perceptual Path Length proposed by StyeGAN.

# Project Progress
So far, this is a couple days' work and a few days of training, but I think it is already somewhat interesting. Expect updates whenever I have a few Colab GPUs to allocate to this (I am usually using all 4 for other projects). I should have some time for this mid-December, so I will try to get some results from: longer training on current configurations, training with lower network capacities (to deal with the pervasive mode collapse), some training on higher (512x512) resolution where applicable, and training current configurations with lower learning rates where useful (while demonstrating divergence due to high learning rate is useful (particularly for the afhq-dog model), there is value in showing the result on the same configuration with a tuned learning rate, however I don't intend to commit the time to tuning the learning rate for every model - these things take forever to train even with optimal learning rates).

# Keywords
1. Latent Representation of an image : Dimensionality Reduction
2. Latent Space : Represtation of compressed data (We can visualize the latent space using algorithms such as t-SNE and LLE, which takes our latent space representation and transforms it into 2D or 3D )
3. Z spaces : A z vector is nothing but a vector containing random values from a Gaussian (normal) distribution. The z-vector is often passed as an input into a fully trained GAN generator model following which the model spits out a real-looking fake image.
4. Style codes/Style vectors : instead of passing the z-vector directly into the generator (which, FYI, is sometimes also called a synthesis network in StyleGANs paper), it is first passed through a mapping network to produce a w-vector AKA style code AKA style vector. This is then injected into the synthesis network at various layers (after undergoing some layer-specific transformations) and the output we get is an awesome high-fidelity image.
5. Latent Space Interpolation : Simply take two latent codes, which could be the codes for images of you and your favorite celeb. Now in a well-developed latent space, these two points would be far because chances are, you look nothing like your favorite celebrity. However, you can pick a point (in space) between these two points, feed it to the Generator and create an intermediate output. Sort of like a mashup of you and your celeb crush, (or a love-child) if you may! This is what latent space interpolation is all about- smooth transitions between two latent codes in latent space.
# Dataset Curation (LPIPS + CLIP)

# Latent Space Interpolation Direction Vectors
1. Trained ResNet to predict latent representations of images
2. Pre-trained Resnet network is used for transforming a reference image and generated image into high-level features space
3. Loss is calculated as a difference between them in the features space
4. Optimization is performed only for latent representation which we want to obtain.
5. Upon completion of optimization you are able to transform your latent vector as you wish. For example you can find a "smiling direction" in your latent space, move your latent vector in this direction and transform it back to image using the generator.
<img width="1247" alt="Style_gan_latent_space" src="https://user-images.githubusercontent.com/13198518/154794876-dd2aefe0-b455-4ce3-8f1c-c061585d20fe.png">

# StyleGAN2 vs StyleGAN #
1. summary and key insights
2. StyleGAN2’s methods
3. Normalization method instead of AdaIN
4. A high-resolution image generation method instead of Progressive Growing
5. Path Length Regularization to smooth latent space

