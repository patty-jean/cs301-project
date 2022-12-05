Milestone 4: Model Compression

A data scientist’s repertoire must contain model compression if they want to be called a data scientist. While seemingly counterintuitive, as model compression suggests the loss of data, it often improves the accuracy of the model while saving computational resources. Milestone 4 challenges the students of CS301-101 to compress their models via knowledge distillation on NNI. The following documentation follows Group 4’s attempt to complete knowledge distillation and their results with model compression. 

Knowledge distillation involves training a larger model (“teacher” model), which is then mimicked by a much smaller model (“student” model). The “teacher” model, while a fairly good model of the data, often takes too much time and is cumbersome to use efficiently. The “student” model learns from the “teacher” model and then is fine-tuned by the distillation process. Knowledge distillation is better than simply making a smaller “teacher” model, as knowledge distillation allows the “student” model to learn what a larger “teacher” model generalizes and apply itself. The knowledge from the “teacher” model is transferred to the “student” model by training the “student” on a transfer data set that contains a soft target (which is created by the “teacher” model). By passing this knowledge from “teacher” to “student”, the “student” can even make predictions on data that itself has never seen before, as it knows what the “teacher” model would generalize the data. 

Group 4 started Milestone 4 by following the instructions on Dr. Monogioudis’ Semantic Segmentation of Satellite Data. After reading Distilling the Knowledge in a Neural Network (Hinton, Vinyals, Dean. 2015), Group 4 felt confident in their knowledge of the worth of distilling knowledge to smaller models. Group 4 started editing their Colab notebook and immediately ran into an import problem. It seems in the two weeks since Milestone 3, Torchmetrics had been updated. This update included removing precision_recall from their functional library. Team 4 avoided this problem by realizing they never did use that import and moved on. Thus, the real Milestone 4 experience began. 

Team 4 performed extensive research into learning how to use TensorFlow to compress their model. While Dr. Monogioudis had provided the important resource of “Knowledge Distillation on NNI”, Team 4 soon found that was only implemented in PyTorch. Unfortunately, TensorFlow’s Keras does not provide the same functionality as PyTorch with NNI. Thus, Team 4 had to decide to simply do model compression rather than the full knowledge distillation process. NNI does not support the pruning of the model with TensorFlow. Despite this deviation from the original assignment, Team 4’s compressed model still managed to improve computational efficiency. 

The following ten images are from the implementation of the compressed model.
![output0(1)](https://user-images.githubusercontent.com/117039859/205525024-02f50df7-4e6d-4151-85c2-b56015fbf7ad.png)
![output1(1)](https://user-images.githubusercontent.com/117039859/205525028-13ff1b47-dd42-4875-9ab5-29d44db26df8.png)
![output2(1)](https://user-images.githubusercontent.com/117039859/205525033-ec30d2c9-eefa-400c-8683-bda848190b60.png)
![output4(1)](https://user-images.githubusercontent.com/117039859/205525040-344f3c53-c1f1-44f7-9f9c-78c73c660bcc.png)
![output6(1)](https://user-images.githubusercontent.com/117039859/205525044-8507f8fd-d680-4b9d-8c56-37cb5cddbdc8.png)
![output3(1)](https://user-images.githubusercontent.com/117039859/205525048-2911c8a7-46f4-42b3-8491-754c3d25a422.png)
![output5(1)](https://user-images.githubusercontent.com/117039859/205525056-c78b9fd2-cf78-49fa-b06a-cc535a213a7c.png)
![output9(1)](https://user-images.githubusercontent.com/117039859/205525067-504daea1-5b5c-4e08-b525-f2053e6955fa.png)
![output7(1)](https://user-images.githubusercontent.com/117039859/205525069-0f900cb2-d23f-4d17-a3b8-9b7225289053.png)
![output8(1)](https://user-images.githubusercontent.com/117039859/205525074-b6217dc2-5f4c-4664-8b09-71244bf5f0bc.png)

The compressed model’s training and validation loss vs epochs. 
![LossvEpochs(1)](https://user-images.githubusercontent.com/117039859/205525176-5e8fbf7a-392a-4652-8755-7e1c50665d49.png)

The compressed model’s precision and recall curve.
![PrecisionvsRecall(1)](https://user-images.githubusercontent.com/117039859/205524997-01ad022b-cfb0-4fdf-b03a-2bf55eb528db.png)

The compressed model significantly reduced the amount of computational resources that Team 4’s previous model had used. While the model did take about the same time, the results of the compressed model improved prediction accuracy of the satellite images. Team 4 would assert that the compressed model did better than their clunky “teacher” model. Milestone 4 was an incredibly enriching experience for the team, and the results were overwhelmingly positive. Team 4 is happy to say that they improved their skills as data science students and thus declares that Milestone 4 was successful. 

                                                                                                                                                                                                                       
