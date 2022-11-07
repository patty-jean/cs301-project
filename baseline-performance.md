Milestone 2.

The work continues on Semantic Segmentation of Satellite Imagery as Team 4 performed baseline segmentation. 

Team 4 made the executive decision to upgrade to Colab Pro on both of their accounts to increase the amount of RAM for their runtime of segmentation. Without Colab Pro, epoch size would have had to be limited to 5, which Team 4 thought was too significant of a decrease. Team 4 kept 100 epochs from the original code, as this number seemed large enough to do an appropriate baseline.  

Team 4's approach to baseline segmentation followed a straightforward method. First, we did a detailed review of the Kaggle dataset. The review included an afternoon of understanding the specifications and each element included. Secondly, we reviewed the Youtube guide "228 - Semantic segmentation of aerial (satellite) imagery using U-net" (found at https://www.youtube.com/watch?v=jvZm8REF2KY, we recommend subscribing if you haven't already). Starting off the video, the eloquent DigitalSreeni walks viewers through a quick summary of the dataset and U-net (pronounced unit). The dataset is not particularly large, containing only 72 images. However, these images need preprocessing. The small amount of images are different sized, placed in 8 different tiles in which they all relatively fit. Additionally, masks contain 6 classes (Building, Land, Road, Vegetation, Water, and Unlabeled) which are in different HEX codes. (Masks correspond to images, and are basically classifying the image parts into different sections of terrain that are recognizable to humans).

Preprocessing the images includes cropping them by a number divisible by 256 and then using patchify to extract them into patches of 256. Those patches are then put into NumPy arrays. These 256-pixel size images are going to be used for training the model. The images are not overlapping. The same process is used for the corresponding masks, with only slight modifications applied for the mask’s png file and reading colors. 

Next up in preparing for segmentation is converting masks’ HEX codes from HEX to RGB. (We recommend a review of hexadecimal if one hasn’t worked with it in a while.) Those RGB values are then converted into integer labels (0-5) to further solidify classes to the same type. After those integers are labeled, they are put into one hot-coded category. 

Finally, the dataset and labels are split into training and testing data. Now, the model is set up. The baseline segmentation hasn’t yet delved into different class weights leaving the model to be expanded. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Team 4’s results for baseline segmentation were fairly decent. Just by looking at the test image, the testing value, and then the predicted image, the baseline segmentation does a fair job of identifying key classes within the picture. In certain images, it seems to be even better than the test label at identifying the roads in pictures. Below are the 10 segmented images from the validation set, the masks, and our predictions. 

![output0](https://user-images.githubusercontent.com/84546784/200224214-3a08b915-1bf8-47bc-bbc0-3109146f0215.png)
![output1](https://user-images.githubusercontent.com/84546784/200224233-9ba22ffa-e4a1-4235-b359-3db290d4a603.png)
![output2](https://user-images.githubusercontent.com/84546784/200224238-603d1610-2d74-4ff4-8b34-8c00c94f1b25.png)
![output3](https://user-images.githubusercontent.com/84546784/200224244-ce378088-95ee-4c3b-bc10-671b8b5135e6.png)
![output4](https://user-images.githubusercontent.com/84546784/200224250-6be2e368-e758-4950-bcbc-a1b7d9ba15d6.png)
![output5](https://user-images.githubusercontent.com/84546784/200224256-b559317d-9c10-48dd-a79a-70066a8ff0ca.png)
![output6](https://user-images.githubusercontent.com/84546784/200224261-d5a9bd8e-85d5-47a7-a04e-45df88f4c85e.png)
![output7](https://user-images.githubusercontent.com/84546784/200224269-9ed0cda2-3dd7-4347-9b79-820a2681f926.png)
![output8](https://user-images.githubusercontent.com/84546784/200224277-0aa24794-2f81-46ed-b094-2d6f19624acd.png)
![output9](https://user-images.githubusercontent.com/84546784/200224286-5e852828-bf71-4627-b335-6bd05718ee8a.png)

Our training and validation loss vs. epochs graph is displayed below. The two losses follow pretty much the same path. As epochs increase, the losses decrease. Thus it is expected that the model does a better job as the epochs increase. As our model is trained for longer, it gets better at predicting, as it should do. 

![LossvEpochs](https://user-images.githubusercontent.com/84546784/200224300-e32481a6-bfc5-4390-a188-3a6f569245a5.png)



The precision-recall values caused the most trouble for Team 4, but Patricia and Elizabeth perserved through learning how to appropriately obtain the values and plot them. Below is the result of Team 4's hard work. As expected, with precision decreasing, recall increases. Again, the recall-precision curve enforces the idea that baseline segmentation does a fairly decent job but still has room for improvement. Team 4 can hardly wait to improve it in Milestone 3. 

![PrecisionvsRecall](https://user-images.githubusercontent.com/84546784/200224316-0f674fd9-0e07-4471-99c0-27d0be8fc59c.png)

