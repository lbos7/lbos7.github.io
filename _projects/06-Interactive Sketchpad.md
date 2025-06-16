---
name: Interactive Sketchpad
tools: [Python, OpenCV, MediaPipe]
image: https://lbos7.github.io/media/interactive-sketchpad.gif
description: Created an application that allows a user to add drawings and annotations to a virtual canvas using their hand
---

# Interactive Sketchpad
This project was completed as the final project of Northwestern University's MSAI 495: Computer Vision. The goal of the project was to implement various computer vision techniques and concepts in an application that allows a user to draw on a virtual canvas using their hand.
<br>

## Demo
<center><iframe width="800" height="500" src="https://www.youtube.com/embed/eManR3R7KWY" title="Interactive Sketchpad Demo" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe></center>

## Tools Used
- OpenCV
- MediaPipe Hands model

## Pipeline
When the application is running, webcam frames are captured using cv2.VideoCapture() and fed into the MediaPipe Hands model. If a hand is detected, then the 21 landmark positions (shown in the image below) are updated.
<center><img src="{{ site.url }}{{ site.baseurl }}/media/mediapipe.png"/></center>
One important note is that only the first hand detected on-screen is recognized as the "drawing hand" and is used for landmark updates and interacting with the sketchpad. With this being said, if two hands are detected and the "drawing hand" moves off-screen, then the other hand that is still on-screen is recognized as the "drawing hand". Based on landmark position updates, different user actions can be discerned such as selecting colors, adjusting a slider, or drawing on the screen and the sketchpad can respond accordingly.

## Features
<center><img src="{{ site.url }}{{ site.baseurl }}/media/interactive-sketchpad_window.png"/></center>

 - 7 selectable colors
 - Multi-finger drawing
 - Eraser
 - Clear screen button
 - Adjustable cursor size
 - Exit button

## Usage
When the applcation is running, a user can move their hand on-screen where it can be detected. Once detected, the user can extend their thumb to turn the cursor on (shown below) which also causes the words "Cursor On" to be displayed in green text in the bottom-right corner of the screen.
<center><img src="{{ site.url }}{{ site.baseurl }}/media/toggle.gif"/></center>
If the cursor is turned on, any finger on the "drawing hand" (besides the thumb) can be used for adding annotations if the finger is extended as shown in the example below.
<center><img src="{{ site.url }}{{ site.baseurl }}/media/multi_finger_draw.gif"/></center>
Colors can be selected, buttons can be pressed, and sliders can be adjusted by moving the "drawing hand" index fingertip within the associated region.

## Potential Improvements and Source Code

- Drawing with both hands
- Option to draw on different input videos and images
- Option to save annotated image or video
- Add more features such as shape detection
<p class="text-center">
{% include elements/button.html link="https://github.com/lbos7/interactive-sketchpad" text="GitHub Repo" %}
</p>