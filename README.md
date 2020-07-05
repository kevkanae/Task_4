# Image Classification and Transfer Learning

### In this Article, we use a simple yet interesting approach to Image Classification using Pre-Trained Model

Since its a Menu Driven Program, We take 4 choices as mentioned in the snippet below:

```Choice = True
while Choice:
    print('\033[1m' + """
    1. Train Transfer Learning Model
    2. Test Transfer Learning Model
    3. Image Classification
    4.. Exit
    """)

    Choice = input("What would you like to do? ")


    if Choice == "1":
        Learning()
        print("\n \033[1m" + 'Model Trained')

    elif Choice == "2":
        Test()
        print("\n \033[1m" + "Test Successful")

    elif Choice == "3":
        path = input("Enter Full Path of Image Name With Extention")
        imgclassify(path)
        print("\n \033[1m" + "Image Successfully Classified")

    elif Choice == "4":
        print("\n \033[1m" + "Goodbye") 

        Choice = None
    else:
        print("\n \033[1m" + "Not Valid Choice Try again")
```

1. **Training Your Model Through Transfer Learning**

We first import our pre-trained model VGG16
Due to its depth and number of fully-connected nodes, VGG16 is over 533MB and 574MB for VGG19. This makes deploying VGG a tiresome task.
But since we're using a very less dataset, the code is pretty simple
Code Reference : Here
a. The Pre-trained model already has a set of layers defined, so while we train our own model, we have to freeze the pre-trained layers.

b. Our Dataset is that of Malarial Cells vs Healthy Cells that comprises of 2 classes, Train and Test, each having 2 subdirectories, namely Unhealthy Cells and Parasitized Cells.

c. We create a function 'add()' that adds our own model layers on top of the pre-trained layer.

d. Next step would be Data Augmentation, in our case, images. We use ImageDataGenerator from keras, to augment data. We generate(manufacture) our own data with the existing data which we have. This methodology of generating our own data is known as Data Augmentation.

e. After fitting the augmented data into our model aka. training our model, we test it. A small scale dataset yields only 84% accuracy. We test this by picking a random image from a shuffled validation directory containing both healthy and unhealthy cells. We use the 'pillow' module to open, ImageDraw, show, etc. an image, and as we can see, it is accurate.

No alt text provided for this image
No alt text provided for this image
Feel free to use the code and run it on Jupyter Notebook or Google Colab

2. **Image Classification Using Transfer Learning**

Image classification is a method to classify the images into their respective category classes using some method like : Training a small network from scratch. Fine tuning the top layers of the model using VGG16.

We've written a simple code to classify a given image as to what is present in it aka, load an image with a coffee cup and the code will tell u its a coffee cup.

Note: Pre-trained Model used is here is Xception

a. Load an image from file

b. Convert the image pixels to a numpy array, since an image is basically an array

c. Reshape data for the model, since the model takes in a default shape that ranges by 71 as min and 299 as max

d. Prepare the image for the model, i.e. simpler version of data augmentation

e. Predict the probability across all output classes(from the predefined classes

f. Convert the probabilities to class labels

g. Retrieve the most likely result, e.g. highest probability and print the classification
