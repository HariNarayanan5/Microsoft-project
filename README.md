from sre_constants import SUCCESS # importing packages
import cv2 # importing packages
from cvzone.HandTrackingModule import HandDetector # importing packages

#webcam
cap = cv2.VideoCapture(0) # Used to capture video.
cap.set(3, 1280) # Width of the calculator
cap.set(4, 720)  # Height of the calculator

detector = HandDetector(detectionCon=0.8, maxHands=2) # Used to detect two hands. 

# Loop
while True:
    SUCCESS, img = cap.read() # used to turn on the camera.
    img=cv2.flip(img, 2) # Used to capture the image displayed in the camera.

    # Detection of hands
    hands,img = detector.findHands(img, flipType=False) # Used to correct the mirror camera.
    
    # Display image
    cv2.imshow("Image", img)
    cv2.waitKey(1)
