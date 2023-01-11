# GcoreVideoBufferHandler

## Introduction

GcoreVideoBufferHandler allows you to apply a blur or background on the frames received from the camera in real time.

## Installation

The SDK is installed in the project via CocoaPods.

Podfile:
``` bash
source ‘https://github.com/g-corelabs/ios-video-buffer-handler-SDK.git‘

...

pod 'GcoreVideoBufferHandler'

```
## Init

``` swift
import GcoreVideoBufferHandler

let bufferHandler = GcoreBufferHandler()
```

## Usage

To use the library, you need to set its operating mode and transfer the pixel buffer from the camera:

``` swift
bufferHandler.mode = .blur
bufferHandler.proccessBuffer(pixelBuffer)
```

## VideoBufferHandler modes

Possible modes of operation are listed here.

1. normal
2. blur
3. detectFaceAndBlur
4. blurBackground (available from iOS 15)
5. backgroundWithImage (available from iOS 15)

for blur modes you can set the radius:
``` swift
bufferHandler.setBlurRadius(40)
```

for background modes you need set image for back or nil to remove background,
it is preferable to use images with a ratio of 9 : 16.
``` swift
bufferHandler.setBackgroundImage(backImage)
```
<br />

### **Normal mode**
Does nothing with the stream, use it if the operating modes depend on any factor (the user has disabled background).<br />
 <br />

### **Blur mode**
Blurring all video stream.<br />
<br />

### **DetectFaceAndBlur mode**
Blurring the entire video stream if there is no person's face in the frame. If there is a face, the blurr will not overlap.<br />
<br />

### **BlurBackground mode**
Applies the blur effect to the background of the frame.<br />
<br />

### **BackgroundWithImage mode**
Overlays the set image on the background of the frame.<br />
<br />
