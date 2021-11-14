# GANs refined
In this week's lab, you used a GAN to generate images of people that look like celebrities.

For this homework, you will re-run the lab with modifications to improve the quality of the generated images. The easiest improvements can be made by modifying values in the **_Inputs_** section

### Submission:
1. What changes did you make to the original lab? Did your changes result in higher quality images?  
  
I increased the number of epochs to 10 and increased the size of z latent vector (size of generator input, which subjectively did result in higher quality changes.  
  
Objectively speaking, the average output of the discriminator for the all real batch converges closer to 0.5 as the generator gets better at creating fake images and the discriminator has a harder time discerning between real and fake images. When it gets too difficult to tell the images as fake or real, the discriminator guesses randomly (**D(x)** = 0.5).
![image](https://user-images.githubusercontent.com/64846871/141691001-0d93aed2-a888-47f6-be6a-6de79ba36d4b.png)

![image](https://user-images.githubusercontent.com/64846871/141691287-d7eeafbb-a09e-4cb7-bd1a-e87d2af2bbcb.png)

2. In your own words, how does the Discriminator improve its ability to detect fakes?

The Discriminator improves its ability to detect fakes by being fed both real and fake images and minimizing a trainable loss function that identifies whether the given image is real or fake. Through backpropagation, the Discriminator tells the Generator how to tweak each pixel so the image will be more realistic. As the Generator gets better, the Discriminator should theoretically also improve its ability to detect fakes.

3. Share a copy of the outpt image from the last step in the notebook (can be an upload to the ISVC Portal, or a link to the file in AWS Object Store).  
  
Attached above.
