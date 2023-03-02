# Anomaly-detection-with-Autoencoder
Imagine the following situation, we need a system that accepts an image of the retina, if the image is not a photo of the retina, then we need to inform the user about the error and not accept this image.
The idea is that if the autoencoder can learn the internal representation of data, such as retinal photographs, then when recovering data that is not a retinal photograph, the error will be much larger. By setting the threshold for this error, you can separate the necessary photos from the unnecessary ones.

MedMNIST is a set of medical datasets in the same MNIST format: image size 28x28 compatible with Pytorch. It has two datasets: RetinaMNIST and BloodMNIST. The first contains images of the retina, the second of blood cells. Despite the declared compatibility with Pytorch, datasets do not have targets and data properties. But there is a dictionary info.
![My Remote Image](https://drive.google.com/file/d/1aMSLAmI-4Gl5_NlP2TKs5whhPIGy5SsC/view?usp=share_link)

The shape of the blood cells is vaguely reminiscent of a photo of the retina. Imagine that when collecting a new portion of data, photos of blood cells mistakenly ended up in a folder with photos of the retina and were included in the new version of the dataset. It is necessary to correct the error and separate the photo of retinal cells from the photo of blood cells.
To do this, you need to train an autoencoder on that part of the dataset that was collected earlier and does not contain errors. Let it be train_retina_dataset and val_retina_dataset. I trained an autoencoder on them.
