# Problems

**Use a static resource to display an image on a Visualforce Page**

Upload the specified zip file as a static resource and display an image from the file on a Visualforce page.

**Challenge Requirements**

* Create a new Visualforce page:
    - Label: **ShowImage**
    - Name: **ShowImage**
* Upload **this file** as a static resource with the name **vfimagetest**
* The page must have a Visualforce **apex:image** tag that displays the **kitten1.jpg** image from the cats directory of the static resource


# Solution

Visualforce page you need that loads the **kitten1.jpg** image from the **cats** subdirectory of the static resource named **vfimagetest**:


# 🖼️ Visualforce Page: ShowImage

``` html
<apex:page>
    <apex:image url="{!URLFOR($Resource.vfimagetest, 'cats/kitten1.jpg')}" />
</apex:page>

```

# ✅ Key Details
* $Resource.vfimagetest references the static resource you uploaded.

* URLFOR(..., 'cats/kitten1.jpg') navigates to the image inside the cats folder.

* This page assumes that the resource was uploaded as a .zip file containing cats/kitten1.jpg.

Need help zipping and uploading the resource or want to style the image with size and alignment?