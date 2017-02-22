#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./write-up-image/grayscale.jpeg "Grayscale"
[image2]: ./write-up-image/blur-gray-image.jpeg "Blured Image"
[image3]: ./write-up-image/edges-image.jpeg "Edges Image"
[image4]: ./write-up-image/masked-image.jpeg "Masked Image"
[image5]: ./write-up-imaga/line-image.jpeg "Lined Image"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale.

![alt text][image1]

After getting back grayscale image, I applied the Gaussian blur, which blurs the image to reduce the noise and detail.

![alt text][image2]

Once we get back the blurred image, i used the Open CV library to use Canny edge detection. Canny edge uses image's pixel gradient to detect edges.

![alt text][image3]

Now we masked the parts of the images that we are not going to need by passing in vertices as parameter.

![alt text][image4]

Finally I drew the line, but modified the function to get more consistant and full length lines. First I seperated the lines from being left or right lines. I did that by using the slopes as parameter. I put a tight parameter to reject any outliers in the slope. Once we got the line using the scope and the intercept, we used the cv2 library to draw the line and apply the line over the original image.

![alt text][image5]



###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

One potential shortcoming happens due to the fact that we hard code the vertices for masking. The lane detection would not work correctly if there was a very tight turn.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

The potential improvement can be creating a dynamic masking that generates new vertices by the angle of the steering wheel.