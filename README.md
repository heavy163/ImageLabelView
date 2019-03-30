# ImageLabelView
[![](https://jitpack.io/v/SirLYC/ImageLabelView.svg)](https://jitpack.io/#SirLYC/ImageLabelView)

A view for data-labeling(a tool for machine learning).

[Chinese blog here.](https://juejin.im/post/5c9f57c251882567d41ebab6)

![1](https://github.com/SirLYC/ImageLabelView/blob/master/images/1.gif?raw=true)
![2](https://github.com/SirLYC/ImageLabelView/blob/master/images/2.gif?raw=true)

## Install
**Step 1.** Add it in your root build.gradle at the end of repositories:

``` gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}
````
**Step 2.** Add the dependency

``` gradle
dependencies {
    implementation 'com.github.SirLYC:ImageLabelView:{latest version}'
}
```
## Use
> You can check [sample code](https://github.com/SirLYC/ImageLabelView/tree/master/sample) here

**Step1.** Add to your layout

Just write like this. **No custom attributes** for now.

**Step2.** Set an image to the view

Set a bitmap to the ImageLabelView, and it will start to show this phone like a imageView with **center inside mode**. The bitmap can be null, which will let the view clear old labels...
```kotlin
val bitmap: Bitmap? = ... // download or read from disk
label.setBitmap(bitmap);
```

**Step3.** Do your job in different mode

When a nonnull bitmap is present, there are 4 modes to operate a image.
- PREVIEW<br>
This is default mode. Everytime a new bitmap is set to this view, the mode will change to it.
In this mode, you can move or scale the image to the perfect position and size for labelling.
- DRAW<br>
In this mode, you can draw a new label. Take rectangle for example. When your finger touch the screen and move, there will be a rectangle right on the image whose left and top is your start posintion and right and bottom is your end position.
After your finger up, the view will immediately change to SELECT mode.
- UPDATE<br>
In this mode, you can resize or change label's position. Take rectangle for example, you can drag a regtangle' vertext or a egde to resize it, or move the whole of the rectange (when your finger down right in the rectangle).
- SELECT<br>
When click or long press, a rectangle at your finger's position will be selected (if drawing end, the new-created label will be selected automatically.). When a label is selected, you can get it by
``` kotlin
label.selectingLabel()
```
At this time, you may let user to input or do other things to change the message of the label or just delete it.

### Step4: Collect your data
Just get the label and call it's **getData()** or get its **message property**!

## Todo/Fix
- [ ] fix state loss after config changes (such as screen orientation, languages...)
- [ ] circle label
- [ ] triangle label
- [ ] other polygon label...

## License
MIT License

Copyright (c) 2019 Liu

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
