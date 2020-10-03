# Face-Classification
Face Classification using Computer Vision Techniques. The code is present in Face Classification using Computer Vision Techniques.ipynb

This assignment is broken down into four main parts:
1. Construct dataset of faces.
2. Build some feature representations using handcrafted techniques.
3. Use and compare the feature representations in context of classification of faces and assessing similarity between faces.
4. Discussion.

## Handcrafted features are properties that can be algorithmically extracted from the image. 
In this assignment we will experiment with Histogram of Oriented Gradients (HOG) feature descriptors. The features learned from data are
features that are learned by finding patterns in multiple images.


## Build a faces dataset
The notebook contains a cell that downloads the VGG Face Dataset.
Search across this dataset for favorite celebrities to build a small dataset that will be used throughout assignment.
• 20 training and 10 testing images of person A
• 20 training and 10 testing images of person B
• 10 testing images of person C, who looks similar to person A
• 10 testing images of person D, who looks similar to person B

Persons C and D share some characteristics with person A and B, respectively, e.g. both male, same
hair type, both wearing glasses, etc. Use OpenCV to detect the faces in the images and
extract the faces. Make
sure that you have some interesting differences between the faces of person A and B and
within each group. Having variability will make it easier to evaluate the representativeness
of the feature representations that you will build in the next section. Make sure to plot a nice
overview of all the faces used, use labels/titles and explain why you chose these individuals.


## Build feature representations
Once you know what defines an object or what allows you to differentiate between two objects, it becomes much easier to detect an object in an image. Learning a robust (same features are extracted from the same object in different conditions) and discriminative (different image objects can be easily separated from each other in feature space) feature representation is key to perform automated object detection effectively. Two big classes of feature representation methods can be identified:
• Handcrafted features 
• Features learned from data
Build Handcrafted features on the faces dataset and discuss the design choices and limitations of the feature representations.


### Handcrafted features

Handcrafted feature descriptors are extracted from the image itself, using a specific deterministic algorithm. The algorithms used are determined by the feature engineer and might differ from task to task. To assess if a handcrafted feature is discriminative we compute it for a few images, we then compare the match score (e.g. euclidean distance between the feature representations) and observe if this matches our intuition/domain knowledge. Handcrafted features were commonly used in traditional machine learning approaches and we still see them today in complicated machine learning tasks e.g. doing machine learning on a manifold mesh.
First, we will compute features from pixel intensities in order to learn a representation of local structures present in an image. Ideally, such a (local) feature descriptor will hold the robust and discriminative property and will additionally be invariant to e.g. illumination, pose, scale, to allow you to detect objects of interest in virtually any given image using that descriptor. We should build one handcrafted feature descriptor from one of these two state-of-the-art handcrafted image feature descriptors:
• Histogram of Oriented Gradients
• Scale Invariant Feature Transform

Second, detecting an object of interest in a new image involves matching the local descriptors
to the image, this allows you to detect which regions have structures that correspond well
to the ones present in your feature descriptor. As a distance metric we could for instance
calculate the euclidean distance between the feature outputs and the feature outputs of your
object(s) of interest at every position in the image.

### Exploit feature representations
Test images from the faces dataset that we built previously. Use favorite classification algorithm and distance metric.

Classification
In classification it is our goal to assign a class to an unseen data example. In this exercise
we will train a binary classifier that can recognise person A (class 0) and person B (class
1). Discuss how we build this classifier for each of your feature representations. Then run
predictions on your test set and compute the mean accuracy. How well does the model
predict on test images of person C and D? Can you explain why and how the three feature
representations behave differently?

Identification
In an identification setup the goal is to compute similarity scores between pairs of data
examples and use them to identify new images. In this exercise we will compute the feature
representation of every image and create a data space using your training data, give each of
the data points a label based on the person they contain. Next we try to identify the test images
using the k-Nearest-Neighbor technique in this data space.


Additional Task
• Pick one feature representation and try to improve your classification/identification
results.
• Modify/add test images to understand what breaks your classifier (e.g. apply additional
variations to your test images such as different lighting, rotations, partial obstruction
of the faces or person wearing glasses etc), explain what is happening and why it is
happening.
• Discussion

