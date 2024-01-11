# OpenCV Face Recognition tutorial with Python using Haarcascades

OpenCV come with a trainer. On OpenCV's GitHub page you can find some trained classifier XML files.  
You can find OpenCV's GitHub [here](https://github.com/opencv/opencv/tree/master/data/haarcascades), we will be using the *haarcascade_frontalface_default.xml* file.  

1. Go to link
2. Open the file `haarcascade_frontalface_default.xml`, see file in **Raw** save it into the folder of the project you are working on
3. We start the project with the very minimal code to load an image
   ```python
   import cv2
   # Read the input image
   img = cv2.imread('test.png)

   # Display the output
   cv2.imshow('img', img)
   cv2.waitKey()
   ```
4. Then we define our classifier as follows, this line of code is below the import
   ```python
   import cv2

   # Define classifier (trained classifier)
   face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
   
   ...
   ```
5. Because this classifier will work with the grayscales images, we convert our image into a grayscale image.  We then detect the faces inside this image.
6. ```python
   img = cv2.imread('test.png')
   ...
   ```
