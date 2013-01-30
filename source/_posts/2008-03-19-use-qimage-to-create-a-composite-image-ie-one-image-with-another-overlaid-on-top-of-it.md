---
title: >
  Use QImage to create a composite image (i.e. One image with another overlaid on
  top of it.)
author: Bennett Smith
layout: post
permalink: >
  /2008/03/use-qimage-to-create-a-composite-image-ie-one-image-with-another-overlaid-on-top-of-it/
categories:
  - How To
  - Qt
---
<span class="alignright"><a target="_blank" href="http://www.trolltech.com"><img src="http://idvlpsw.files.wordpress.com/2008/03/qt.png" alt="qt.png" border="0" width="48" height="48" /></a></span>Today I wanted to combine two images of similar size to create a new image. The new image was going to be used for a toolbar button. I have purchased a set of commercial images in the PNG format for use on application toolbars. The set came with a bunch of overlay images that could be used to modify each of the base images. The overlays included things like arrows, warning signs, arrows, people, etc. My first though for using these images was to fire up Adobe Illustrator and just create a new icon by merging the base and overlay together. Then I realized that Qt could do the job for me at runtime, and with a little work I could dynamically overlay different badges on a base icon. 

The code below can be used to construct a composite image. You pass in references to a base image and an overlay image. These images are used to construct a third image, and that is returned to the caller.

<pre>QImage createImageWithOverlay(const QImage& baseImage, const QImage& overlayImage)
{
    QImage imageWithOverlay = QImage(baseImage.size(), QImage::Format_ARGB32_Premultiplied);
    QPainter painter(&imageWithOverlay);

    painter.setCompositionMode(QPainter::CompositionMode_Source);
    painter.fillRect(imageWithOverlay.rect(), Qt::transparent);

    painter.setCompositionMode(QPainter::CompositionMode_SourceOver);
    painter.drawImage(0, 0, baseImage);

    painter.setCompositionMode(QPainter::CompositionMode_SourceOver);
    painter.drawImage(0, 0, overlayImage);

    painter.end();

    return imageWithOverlay;
}
</pre></p> 

Here is an example of using this routine to create an image that might be used to represent something being transfered from a network attached machine.

<pre>QImage baseImage(":/Resources/connect_pc_64.png");
    QImage overlayLogoff(":/Resources/overlay_arrow_east_64.png");
    QImage logoffImage = createImageWithOverlay(baseImage, overlayLogoff)
</pre>

The two source images and resulting composite are shown below.

1.  :/Resources/connect\_pc\_64.png
<img src="http://idvlpsw.files.wordpress.com/2008/03/connect-pc-64.png" border="0" width="64" height="64" />

2.  :/Resources/overlay\_arrow\_east_64.png
<img src="http://idvlpsw.files.wordpress.com/2008/03/arrow-east-64.png" border="0" width="64" height="64" />

3.  Generated Composite Image
<img src="http://idvlpsw.files.wordpress.com/2008/03/logoffimage.png" border="0" width="64" height="64" />

