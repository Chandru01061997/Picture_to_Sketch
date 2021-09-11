
# Image to Pencil Sketch Conversion with Python

### Sample output of our code

![sample](https://user-images.githubusercontent.com/77289751/132935424-8da95c53-7e34-4b65-a76d-ade542aecc17.jpg)



We need to read the image in RBG format and then convert it to a grayscale image. This will turn an image into a classic black and white photo. Then the next thing to do is invert the grayscale image also called negative image, this will be our inverted grayscale image. Inversion can be used to enhance details. Then we can finally create the pencil sketch by mixing the grayscale image with the inverted blurry image. This can be done by dividing the grayscale image by the inverted blurry image. Since images are just arrays, we can easily do this programmatically using the divide function from the cv2 library in Python.

Reqirements:
* Basic Idea on OpenCV
* Knowledge in Python

Lets proceed with the code.

1. Install OpenCV in your system using the command
`pip install opencv-python`

2. Now import the OpenCV library
`import cv2`

3. In this I have used two images one is iron man, other is the pic of Sang Chi you can also use your own picture from your system

`original_image = cv2.imread('IRONMAN.jpg')`

once you have read the original RGB image then you should convert it to grayscale image

`greyscale_image = cv2.cvtColor(original_image, cv2.COLOR_BGR2GRAY)`

next you should convert it to negative image

`negative_image = cv2.bitwise_not(greyscale_image)`

followed by converting it to blur image 

`inv_image = cv2.GaussianBlur(negative_image, (15,15), 0)`
`blur_image = 255 - inv_image`

After that diving the greyscale_image and the blur image will give you the desired sketch image since at the benckend this pictures are all array 

`sketch_image = cv2.divide(greyscale_image, blur_image, scale = 256.0)`

finally you can see the image either by saving the immage in the same folder or directly visualizing it

`cv2.imwrite("Pencil_Sketch.jpg", sketch_image)` for saving the image

This is for visualizing the image 

`cv2.imshow("Pencil_Sketch.jpg",sketch_image)`

`cv2.waitKey(0)`

`cv2.destroyAllWindows()`

Once everything is done you will obtain the result as shown below


## Screenshots

![Final_output](https://user-images.githubusercontent.com/77289751/132935317-7505e1a5-3f3c-4018-9765-02360b86439f.png)

  