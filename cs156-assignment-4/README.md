# Assignment 4

## Assignment instructions:

### Machine Learning Fashionista

This assignment builds on the pre-class work from [this](https://github.com/minerva-university/cs156/tree/master/session07) week.

It might be useful to read through [this example](http://scikit-learn.org/stable/auto_examples/decomposition/plot_pca_vs_lda.html) before attempting this assignment.

#### Instructions

- Split your dataset from the PCA pre-class work into 80% training data and 20% testing data.
- Build a simple linear classifier using the original pixel data. There are several options that you can try including a [linear SVC](http://scikit-learn.org/stable/modules/generated/sklearn.svm.LinearSVC.html#examples-using-sklearn-svm-linearsvc) or a [logistic classifier](http://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html#examples-using-sklearn-linear-model-logisticregression). Both of which will be covered in more detail later in this course.
  - What is your error rate on the training data?
  - What is your error rate on the testing data?
- Train the same linear model as in the question above, but now on the reduced representation that you created using PCA.
  - What is your error rate on the training data?
  - What is your error rate on your testing data?
- Train the same linear model as the first question again, but now on the reduced representation that you created using LDA.
  - What is your error rate on the training data?
  - What is your error rate on your testing data?
- Write three paragraphs describing and interpreting your results from the three models. Make a recommendation on which classifier you would prefer, and why.

Please convert everything to a single PDF file and submit it. Be sure to include all the code necessary to reproduce your results, but please leave out exploratory code that does not contribute to any figures or final results. This assignment is not just about code, and any choices which need justification, or insights you gain should be included in plain English.

### Notes:
**Regarding data pre-processing: there are several ways to load and process image data; the following is just one way if you are feeling lost.**

- Using `listdir` from the `os` module, generate a list of each image's name, path included, for easy passing to an image processor. You might want to use the Python Imaging Library (PIL) to open images.
- *Note:* images are big, so you can't keep so many open in memory at once. Instead, use a loop, and open images one by one, resize to a uniform size, append to an array (`np.asarray()` will extricate the RGB channels from each pixel in the original image), and then call `Image.close()` to free up the used memory.
- You might want to aim for an array of four dimensions: (num-images, height, width, 3) -- where the first dimension is the number of images you use, and the height/width are up to you. The fourth dimension, of size 3, will be RGB values for each pixel.
- Since you will classify the images, you'll need to label them appropriately. There are many ways to do this. One is to save the labels in their own dimension. Another is to save all your data in a Bunch dictionary, which allows dot-accessible attributes (i.e., so you'll save your data as a numpy array as one attribute, labels as another). Look at scikit-learn's toy datasets, e.g., the MNIST digits or iris data, for an example of this. Another option is to put images from one category into its own directory, and images from another category into another directory.
- Eventually, if you are using a scikit-learn implementation of the algorithms (which you needn't do; you could always implement them yourself!), you will need to find a way to make your data scikit compatible. Recommendation: consider reshaping your array to a 2D matrix: (number of images, 3*number of pixels), where in the second dimension, you've spread out your height * width * 3 channels into one long "row" representation.

Later in this course we will revisit this problem using methods which are currently state-of-the-art and significantly improve your results!