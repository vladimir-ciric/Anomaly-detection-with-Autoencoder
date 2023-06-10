# Anomaly-detection-with-Autoencoder
Imagine the following situation, we need a system that accepts an image of the retina, if the image is not a photo of the retina, then we need to inform the user about the error and not accept this image.
The idea is that if the autoencoder can learn the internal representation of data, such as retinal photographs, then when recovering data that is not a retinal photograph, the error will be much larger. By setting the threshold for this error, you can separate the necessary photos from the unnecessary ones.

MedMNIST is a set of medical datasets in the same MNIST format: image size 28x28 compatible with Pytorch. It has two datasets: RetinaMNIST and BloodMNIST. The first contains images of the retina, the second of blood cells. Despite the declared compatibility with Pytorch, datasets do not have targets and data properties. But there is a dictionary info.

<img width="829" alt="retina" src="https://user-images.githubusercontent.com/95381758/222410320-e8a63518-a258-4b22-a55f-d114e6000ddf.png">

<img width="819" alt="blood" src="https://user-images.githubusercontent.com/95381758/222410347-97fe74bd-61b8-4370-a78d-1ce64f0eb1f3.png">


The shape of the blood cells is vaguely reminiscent of a photo of the retina. Imagine that when collecting a new portion of data, photos of blood cells mistakenly ended up in a folder with photos of the retina and were included in the new version of the dataset. It is necessary to correct the error and separate the photo of retinal cells from the photo of blood cells.
To do this, you need to train an autoencoder on that part of the dataset that was collected earlier and does not contain errors. Let it be train_retina_dataset and val_retina_dataset. I trained an autoencoder on them.

After training the autoencoder, the following results were obtained for images of the retina and blood cells:

<img width="825" alt="retina_res" src="https://user-images.githubusercontent.com/95381758/222410673-c986820e-3525-4835-b930-82bc7af48493.png">

<img width="821" alt="blood_res" src="https://user-images.githubusercontent.com/95381758/222410705-b8ba7e1a-ffda-498b-b3dd-61f7213df948.png">

As a result 0 images out of 120 were droped from retina dataset (0%) and 3270 images out of 3421 were droped from blood dataset (96%).
