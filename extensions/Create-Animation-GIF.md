---
layout: page
lang: en
title: Create Animation GIF
---

# {{ page.title }}

In this article, we're creating an animation GIF file
from a scanned image of a handwritten picture.

Here is a JPEG image file that contains animation frames:
[cat-picture.jpg](../images/cat-picture.jpg).  
_(Any size of picture would be acceptable
if only all the frames have the same size and are aligned at regular invervals.)_

![cat-picture](../images/cat-picture.jpg)


The program needs to do the following jobs.

* Reads a JPEG file as a source image.
* Reduces number of colors in the image down to 256 so that it suits GIF specification.
* Creates a GIF content.
* Divides the source image into frames and adds them to the GIF content.
* Writes the GIF content to a file.

And here is the script code:

    import(jpeg)
    import(gif)
    
    delayTime = 12      // interval time in 1/100 seconds
    [nx, ny] = [6, 2]   // number to divide a source image
    img = image('cat-picture.jpg').reducecolor(`win256)
    [w, h] = [img.width / nx, img.height / ny]
    n = nx * ny
    x = range(nx).cycle(n) * w
    y = int(range(n) / nx) * h
    gif.content().addimage(img.crop(x, y, w, h), delayTime).write('cat-anim.gif')

![cat-picture](../images/cat-anim.gif) [cat-anim.gif](../images/cat-anim.gif)