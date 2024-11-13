# Capstone-3-Concrete

## Description
This capstone project is a simple CNN or Computer Vision project to classify concrete crack based on data from (https://data.mendeley.com/datasets/5y9wdsg2zt/2) using Tensorflow.Keras. (its also my third time posting here)
The architure of this model is a simple CNN model consist of Convolutional layers and Pooling layers. Details will explained further.

## The process of how this model training been done

1. Import Packages
   - Import libraries that might be useful for this model (dunno la)
     ![Import Libraries](https://github.com/user-attachments/assets/dd93118e-25bb-4676-8403-be18c80462cb)

2. Data Loading
   - Load the given dataset from (https://data.mendeley.com/datasets/5y9wdsg2zt/2)
   - This is the code to load data from this website
     ![Load Data](https://github.com/user-attachments/assets/a66c2a49-c73d-49d1-8f65-da3cf5694259)
   - We split the dataset early on 80/20, training and testing.
   - We also set the default image at 180, 180 with a batch size of 32 (smaller resolution make it faster to train, but less accurate. But... eh no worries, we have thousands of data for this model, should be good.... Right?)
  
3. Configure the datasets
   - we need to optimize the data loading process by caching and prefetching the dataset to improve training performance.
     ![Configuration](https://github.com/user-attachments/assets/69602c94-0b4a-4ff5-b43b-10d60bfb165b)

4. Model Development
   - As promised, I will explain further detail in this part, on how this model work
   - We used a Sequential keras model and set the input shape based on image resolution we set before but with RGB depth added (Well, its have color, duh ofc)
   - The CNN Layers consists of Convolutional Layers and Pooling Layers. So what these layers do actually?
        - CNNs perceive images as volumes, treating them as 3-dimensional objects. For example, a color image can be viewed as a volume with width, height, and depth (channels like Red, Green, and Blue).
        - Convolutional layers apply filters (kernels) to the input image in order to extract important features such as edges, textures, and patterns. These filters are small, learnable matrices that detect specific features in the image.
        - The convolution operation involves sliding these small filters (kernels) over the input data (e.g., an image) to produce a feature map. This process highlights the presence of specific patterns, such as edges, corners, or textures, in different regions of the             image.
        - Then, this convolution layer always paired up with pooling layer.
        - This pooling layer then downsample the feature maps produced by the convolutional layers, reducing their spatial dimensions (width and height) while retaining important information. This helps make the network computationally more efficient and reduces the                complexity of the model.
        - Why we need this pooling layer. Well I tell ya, its for Dimensionality Reduction (reducing size) and Prevent Overfitting (making model not remember small details)
   
![Model Summary](https://github.com/user-attachments/assets/bb3c03d5-3e82-435a-a7b4-c162773cbb87)

   - Then after done that, we flatten it so we can use it in Neural Network.
   - This is the model architecture in total
![Model Architecture](https://github.com/user-attachments/assets/7cf0701b-1a77-4cb9-bd1f-515da100918a)

5. Model Compiler
    - Optimizer = Adam (Default)
    - loss function = sparse_categorical_crossentropy
    - metric = accuracy

6. Setting the callback functions
   - Earlystopping (patience = 3, verbose = 2)
   - TensorBoard - to visualize graphs and easier to compare with previous training
![Callback Functions](https://github.com/user-attachments/assets/f4f9c599-dd15-4c47-b28e-96b4b10485ae)

  
7. Model Training
    - epoch = 100
![Model Training](https://github.com/user-attachments/assets/5c76201c-45ed-4382-8fba-e585f2cf6401)
    - Here are the results from TensorBoard
![Model Epoch Accuracy](https://github.com/user-attachments/assets/a8c22842-37ed-45ce-94cb-c803384c7d0b)
    - Its seems the accuracy graphs for training and validation are converging indicating good fit model
![Model Epoch Loss](https://github.com/user-attachments/assets/a37d162b-4b97-42a1-a30e-01ca2b6b8d79)
    - Also the same for loss graphs training and validation are converging at the end of epoch, which also indicating good fit model
 

8. Model Prediction
   - Now, we finished our model training, we can proceed with the prediction
   - Here we test our model with first ten images from test dataset
![Model Prediction](https://github.com/user-attachments/assets/f6701c81-63ac-4938-8bd4-1eed56fc264a)
   - It seems the model can predict it nicely and correctly

9. Last Step
    - After we satisfied with the results of model prediction, we can save it for future use.
    - Thus I saved the model in h5 format
![Model Save](https://github.com/user-attachments/assets/bbcf3a79-fcff-4d17-9451-52e38fe5dba5)

## Acknowledgements

- Also thanks to my SHRDC Trainers for giving me the opportunity and knowledges about coding, machine learning and deep learning
