---
title: >
  Use QImage to create a composite image (i.e. One image with another overlaid on
  top of it.)
author: bsmith
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

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_19">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fuse-qimage-to-create-a-composite-image-ie-one-image-with-another-overlaid-on-top-of-it%2F&linkname=Use%20QImage%20to%20create%20a%20composite%20image%20%28i.e.%20One%20image%20with%20another%20overlaid%20on%20top%20of%20it.%29" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fuse-qimage-to-create-a-composite-image-ie-one-image-with-another-overlaid-on-top-of-it%2F&linkname=Use%20QImage%20to%20create%20a%20composite%20image%20%28i.e.%20One%20image%20with%20another%20overlaid%20on%20top%20of%20it.%29" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F03%2Fuse-qimage-to-create-a-composite-image-ie-one-image-with-another-overlaid-on-top-of-it%2F&linkname=Use%20QImage%20to%20create%20a%20composite%20image%20%28i.e.%20One%20image%20with%20another%20overlaid%20on%20top%20of%20it.%29" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>