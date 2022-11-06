Milestone 2.

The work continues on Semantic Segmentation of Satellite Imagery as Team 4 performed baseline segmentation. 

Team 4 made the executive decision to upgrade to Colab Pro on both of their accounts to increase the amount of RAM for their runtime of segmentation. Team 4 modified the number of epochs in the original segmentation file from 100 to 5. Team 4 is aware that this significant decrease could affect our baseline performance, but 100 epochs would not have been possible to run in a relatively quick time.

Team 4's approach to baseline segmentation followed a straightforward method. First, we did a detailed review of the Kaggle dataset. The review included an afternoon of understanding the specifications and each element included. Secondly, we reviewed the Youtube guide "228 - Semantic segmentation of aerial (satellite) imagery using U-net" (found at https://www.youtube.com/watch?v=jvZm8REF2KY, we recommend subscribing if you haven't already). Starting off the video, the eloquent DigitalSreeni walks viewers through a quick summary of the dataset and U-net (pronounced unit). The dataset is not particularly large, containing only 72 images. However, these images need preprocessing. The small amount of images are different sized, placed in 8 different tiles in which they all relatively fit. Additionally, masks contain 6 classes (Building, Land, Road, Vegetation, Water, and Unlabeled) which are in different HEX codes. (Masks correspond to images, and are basically classifying the image parts into different sections of terrain that are recognizable to humans).

Preprocessing the images includes cropping them by a number divisible by 256 and then using patchify to extract them into patches of 256. Those patches are then put into NumPy arrays. These 256-pixel size images are going to be used for training the model. The images are not overlapping. The same process is used for the corresponding masks, with only slight modifications applied for the mask’s png file and reading colors. 

Next up in preparing for segmentation is converting masks’ HEX codes from HEX to RGB. (We recommend a review of hexadecimal if one hasn’t worked with it in a while.) Those RGB values are then converted into integer labels (0-5) to further solidify classes to the same type. After those integers are labeled, they are put into one hot-coded category. 

Finally, the dataset and labels are split into training and testing data. Now, the model is set up. The baseline segmentation hasn’t yet delved into different class weights leaving the model to be expanded. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Team 4’s results for baseline segmentation were fairly decent. 
