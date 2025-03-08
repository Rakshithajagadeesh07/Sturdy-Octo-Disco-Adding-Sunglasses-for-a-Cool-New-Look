# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program:

### Name: Rakshitha J
### Reg.No: 212223240135

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('PHOTO1.jpg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
faceImage.shape
faceImage.shape
glassPNG = cv2.imread('ss1.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")
glassPNG = cv2.resize(glassPNG,(290,140))
print("image Dimension ={}".format(glassPNG.shape))
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]
plt.figure(figsize=[10,10])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(121);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
faceWithGlassesNaive = faceImage.copy()
faceWithGlassesNaive[240:380, 270:560] =glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[240:380, 270:560]
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[10,10])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
faceWithGlassesArithmetic[240:380, 270:560]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
## Output:
### 1.Original image:
![1](https://github.com/user-attachments/assets/99cf660d-dfc2-4e67-9c45-2506eb0d5a46)


### 2.Glass:
![2](https://github.com/user-attachments/assets/674377b1-cab8-434c-bb5b-408f5d94ab41)


### 3.Glass color channel:
![3](https://github.com/user-attachments/assets/91cbd580-7e38-4ade-afdf-8f49a9dddbfc)


### 4.Face With Glass:
![4](https://github.com/user-attachments/assets/bc2316c7-4325-4923-b786-1cdaf9c44316)


### 5.Eye and glass region:
![5](https://github.com/user-attachments/assets/27dec402-59e9-4a7e-8ebf-c22a2c019544)


### 6.Final image with glass:
![6](https://github.com/user-attachments/assets/f43320c7-62be-4901-a9f0-a093101ddd6f)


## Result:
Thus, the creative project designed to overlay sunglasses on individual passport size photo has been successfully executed.














