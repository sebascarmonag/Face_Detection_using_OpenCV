# OpenCV Face Recognition tutorial with Python using Haar Cascades 
## Face Recognition on Pictures

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
   ```python
   ...
   img = cv2.imread('test.png')
   gray = cv2.cvtColor(img,cv2.COLOR_BGR2GRAY)
   faces = face_cascade.detectMultiScale(gray, 1.1, 4)
   ...
   ```
6. The last step is to iterate over all the faces which were detected and draw a rectangle.
   ```python
   ...
   faces = face_cascade.detectMultiScale(gray, 1.1, 4)

   for (x, y, w, h) in faces:
      cv2.rectangle(img, (x, y), (x + w, y + h), (255, 0, 0), 3)
   ...
   ```
7. A sample of the all code is below:
   ```python
   import cv2

   # first define classifier
   face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')

   # Read the input image
   img = cv2.imread('disney.jpeg')
   gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
   faces = face_cascade.detectMultiScale(gray, 1.1, 4)

   for (x, y, w, h) in faces:
      cv2.rectangle(img, (x, y), (x + w, y + h), (255, 0, 0), 2)

   # Dispaly the output
   cv2.imshow('img', img)
   cv2.waitKey()
   ```

## Face Recognition on Video  

This process is not different to the picture, the same process will apply on each and every single frame.
1. Instead of read the image, we use a video capture method to read the video.
   ```python
   import cv2

   # first define classifier
   face_cascade = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
   
   # Read the input video
   cap = cv2.VideoCapture('IMG_5074.mp4')
   
   # If you want to connect your camera use 0 instead of a file name
   #cap = cv2.VideoCapture(0)
   
   while cap.isOpened():
       _, frame = cap.read()
   
       gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
       faces = face_cascade.detectMultiScale(gray, 1.1, 4)
   
       for (x, y, w, h) in faces:
           cv2.rectangle(frame, (x, y), (x + w, y + h), (255, 0, 0), 3)
   
       # Dispaly the output
       cv2.imshow('frame', frame)
       if cv2.waitKey(1) & 0xFF == ord('q'):
           break
   
   cap.release() 
   ```

