Milestone 2.

The work continues on Semantic Segmentation of Satellite Imagery as Team 4 performed baseline segmentation. 

Team 4 made the executive decision to upgrade to Colab Pro on both of their accounts to increase the amount of RAM for their runtime of segmentation. Without Colab Pro, epoch size would have had to be limited to 5, which Team 4 thought was too significant of a decrease. Team 4 kept 100 epochs from the original code, as this number seemed large enough to do an appropriate baseline.  

Team 4's approach to baseline segmentation followed a straightforward method. First, we did a detailed review of the Kaggle dataset. The review included an afternoon of understanding the specifications and each element included. Secondly, we reviewed the Youtube guide "228 - Semantic segmentation of aerial (satellite) imagery using U-net" (found at https://www.youtube.com/watch?v=jvZm8REF2KY, we recommend subscribing if you haven't already). Starting off the video, the eloquent DigitalSreeni walks viewers through a quick summary of the dataset and U-net (pronounced unit). The dataset is not particularly large, containing only 72 images. However, these images need preprocessing. The small amount of images are different sized, placed in 8 different tiles in which they all relatively fit. Additionally, masks contain 6 classes (Building, Land, Road, Vegetation, Water, and Unlabeled) which are in different HEX codes. (Masks correspond to images, and are basically classifying the image parts into different sections of terrain that are recognizable to humans).

Preprocessing the images includes cropping them by a number divisible by 256 and then using patchify to extract them into patches of 256. Those patches are then put into NumPy arrays. These 256-pixel size images are going to be used for training the model. The images are not overlapping. The same process is used for the corresponding masks, with only slight modifications applied for the mask’s png file and reading colors. 

Next up in preparing for segmentation is converting masks’ HEX codes from HEX to RGB. (We recommend a review of hexadecimal if one hasn’t worked with it in a while.) Those RGB values are then converted into integer labels (0-5) to further solidify classes to the same type. After those integers are labeled, they are put into one hot-coded category. 

Finally, the dataset and labels are split into training and testing data. Now, the model is set up. The baseline segmentation hasn’t yet delved into different class weights leaving the model to be expanded. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Team 4’s results for baseline segmentation were fairly decent. Just by looking at the test image, the testing value, and then the predicted image, the baseline segmentation does a fair job of identifying key classes within the picture. In certain images, it seems to be even better than the test label at identifying the roads in pictures. Below are the 10 segmented images from the validation set, the masks, and our predictions. 


![output0](https://user-images.githubusercontent.com/84546784/200200747-500fa10b-1c18-42e7-bc9c-2da546c6830a.png)
![output1](https://user-images.githubusercontent.com/84546784/200200751-d0de78de-01f7-4728-8522-71e67123ff59.png)
![output2](https://user-images.githubusercontent.com/84546784/200200754-5df90303-d85f-418a-8d18-f50a9709642e.png)
![output3](https://user-images.githubusercontent.com/84546784/200200757-cdca4479-3f00-4991-9b14-ee0b71a7804c.png)
![output4](https://user-images.githubusercontent.com/84546784/200200761-9cfd406f-e056-48d7-a0b7-517bf0903875.png)
![output5](https://user-images.githubusercontent.com/84546784/200200764-037bb562-4ca6-4062-b248-ebb6b082cfb2.png)
![output6](https://user-images.githubusercontent.com/84546784/200200816-275432d9-a2c0-4f85-91b2-35d65471dea8.png)
![output7](https://user-images.githubusercontent.com/84546784/200200819-29375721-a7f1-4cc4-8a26-d3e1fb4a9909.png)
![output8](https://user-images.githubusercontent.com/84546784/200200822-8be2c3af-14f8-4c1d-b319-5ce9ab19dfb4.png)
![output9](https://user-images.githubusercontent.com/84546784/200200824-9a9dd0ad-2f67-46ec-863e-7116f723a832.png)

Our training and validation loss vs. epochs graph is displayed below. The two losses follow pretty much the same path. As epochs increase, the losses decrease. Thus it is expected that the model does a better job as the epochs increase. As our model is trained for longer, it gets better at predicting, as it should do. 



The precision-recall values caused the most trouble for Team 4, but Patricia and Elizabeth perserved through learning how to appropriately obtain the values and plot them. Below is the result of Team 4's hard work. As expected, with precision decreasing, recall increases. Again, the recall-precision curve enforces the idea that baseline segmentation does a fairly decent job but still has room for improvement. Team 4 can hardly wait to improve it in Milestone 3. 
