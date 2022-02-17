# Virtual Painter using OpenCV3 
An openCV application that uses Python and MediaPipe to detect hands, hand landmarks, and then use them to paint on a live webcam.


Workflow: 
-- Design 4 different images/headers that overlay on the openCV dsiplay as you change painter colors. 

  Eraser Selected:
    ![4](https://user-images.githubusercontent.com/47854973/148497533-98a70961-91dc-47f0-8f94-b59ac6b401f4.png)
  Red selected:
     ![1](https://user-images.githubusercontent.com/47854973/148497534-54e317bb-cdea-49c1-bc82-b4bcab09ba94.png)
  Yellow Selected:
    ![2](https://user-images.githubusercontent.com/47854973/148497536-13774eb5-bee1-45fe-99d9-da4aa6ef8966.png)
  Purple Selected: 
  ![3](https://user-images.githubusercontent.com/47854973/148497537-84ee0982-d0e4-4d31-8ac1-98d46fcc5283.png)


-- Write a program to Open Webcam and use MediaPipe to detect hand's landmarks (HandTracking.py)

-- Convert HandTracking.py to a module (HandTrackingModule.py) with a few modifications. 

    --- class handDetector(): //contains methods to find a hand, detect landmarks and count the number of fingers
         function findHands(): 
                //simply uses mediapipe to detect hands
         function findPosition():
                //uses mediapipe to return a list of landmarks tuples (landmark_Num, x_landmark, y_landmark)
         function fingersUp():
                //You can find the id for each landmark and the finger it corresponds to in the meediapipe 
                documentation
                //If (finger tip detected):
                      finger is up
                  else:
                      finger is down
                      
-- For the main VirtualPainter.py: 

      if (hand detedcted):
          if (finger tips detected):
              count how many fingers up
              if (count == 2):
                  selection mode
                  //now, find the coordinates of the finger tip and if it's close to a certain part of the header
                  //change the color or choose the eraser
              if (count == 1):
                  drawing mode
                  //use openCV line to draw lines but keep updating the new and previous x,y coordinates of
                  finger tips, so lines are not awkward and straight
                  
       //Create three different canvases
       //1. Webcam (img) 2. blank black canvas (imgCanvas) 3. inverse of canvas 2 (imgInv)
       imgCanvas -> grayImg -> imgInv
       img = img biwise& imgInv
       img = img bitwise| imgCanvas

       Display final img.
 

       


