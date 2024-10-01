---
title: HCI Research
publishDate: 2019-12-01 00:00:00
img: /assets/stock-2.jpg
img_alt: A bright pink sheet of paper used to wrap flowers curves in front of rich blue background
description: |
  We paired with a cutting-edge music API and a team of horticulturalists
  to build AI-generated playlists that maximize houseplant health.
tags:
  - HCI
  - Research
---

This blog is part an assigment part of a series of research from the course Human Computer Interface at Institut Polytechnique de Paris.

* I will first present a solution from Hitesh Kumar Sharma and his team about HCI controlled with AI.
* Then, we will approach the ultimate display by Ivan Sutherland.
<blockquote>
  <span style="font-size: 32px;">HCI controlled AI enabled system for optimization </span>
</blockquote>

**Introduction :** 

In today's world, the basic interaction with computer is a keyboard and a mouse. Those tools are really easy to use and that's what made them famous. The only problem is for people with disabilities, those tools can be hard according to the severity of the disability. Also, another limit of a moouse is that we can't use it while moving. These problems lead Hitesh and his team to find a different effective interactive system which will work by controlling the mouse with hand gestures based on image recognition with a computer camera. Some solutions already exists but required to wear gloves which can be annoying in some situations.

**Solution and methods :**

What Hitesh Kumar Sharma and his team developed is a free glove mouse using only image recongition (without physical hardware).
To do such a job, they needed a training dataset. This dataset involved 12000 hand photos of 6 humans (3males and 3 females) with 10 hand gestures types. Due to resources restrictions, only one person sample is selected and 5 different type of gesture are used (ex: thumb down, up...).

The training of the model is based on forward propagation (data received, processed, output produced)
Calculate the error and update the network's parameters for backward propagation.
The formula for the output of a perceptron is the following one and the sigmoid activation function is used.

![alt text](image-1.png)

The implementation is made with OpenCV following different steps : 

* Capturing real time video using a web camera
* Processing image frame
* Flipping of image frame 
* Conversion to grayscale
* Finding contours 
* Counting the number of convexity defects
* Moving the mouse cursor when the number of convexity defects is equal to 2 (using pyautogui)
* Implementing left click and right click.

Example of possible moves : 

No move : 

![alt text](image.png)


Mouse Moving : 

![alt text](image-2.png)

Left Click : 

![alt text](image-3.png)

Right Click : 

![alt text](image-4.png)


The camera detect the number of convexity defects and choose its action in order to it.


**Conclusion :**

The results are relevant as the picture can show : 

![alt text](image-5.png)

So this technology can solve several problem and proved that it can work with efficiency and accuracy. It can be used for many application, and more complex systems.


<blockquote>
  <span style="font-size: 32px;">The Ultimate Display</span>
</blockquote>