# OpenCV (3.2.0) Android SDK Binary with all extra modules
The project includes a built-in Opencv library with all the additional modules from the OpenCV_contrib project. In addition, the project was built with Tesseract, so the 'text' module is available.

### Short Description
When working on a project using the OpenCV library, and in particular the 'text' module available in additional modules from the OpenCV_contrib project, I encountered difficulties while building these libraries together with Tesseract (and Leptonica). The OpenCV binary version of the Android SDK is not available with additional modules from the OpenCV_contrib project, so after a successful attempt I decided to share the binaries.

### Short Usage Description
1. Launch Android Studio and create a new project selecting File -> New -> New Project…
2. Go to File -> New -> Import Module… and provide  ‘<opencv-android-sdk-source>/sdk/java’. Click ‘Next’ and ‘Finish’.
3. Then add the imported library as a dependency to the ‘app’ module in File->’Project Structure’.
4. Copy libraries of OpenCV from ‘<opencv-android-sdk-source>/sdk/native/libs’ into a newly created folder (jniLibs) in side the ‘app/src/main’ folder.

You can follow [**THIS**](https://zami0xzami.wordpress.com/2016/03/17/opencv-for-mobile-devices-using-android-studio/) nice tutorial to create your OpenCV Android Project. 

### Build By Yourself

Building libraries can make you go gray so you act on your own responsibility.

1. First you must have Tesseract installed in your system. In Linux you can do It by installing Leptonica and Tesseract from you system repositories (in Arch from AUR), or by following theese steps:

- Download leptonica 1.70 tarball (helper image processing library, used by tesseract. Later versions might work too):
[**Leptonica**](http://www.leptonica.com/download.html)
unpack and build it:
```
cd leptonica-1.70
mkdir build && cd build && ../configure && make && sudo make install
```
leptonica will be installed to /usr/local.

- Download tesseract-3.03-rc1 tarball from [**HERE**](https://drive.google.com/folderview?id=0B7l10Bj_LprhQnpSRkpGMGV2eE0&usp=sharing)
unpack and build it:
```
export LIBLEPT_HEADERSDIR=/usr/local/include/
cd tesseract-3.03
mkdir build && cd build
../configure --with-extra-includes=/usr/local --with-extra-libraries=/usr/local
make && sudo make install
```
tessract will be installed to /usr/local.

- download the pre-trained classifier data for english language (or other):
https://code.google.com/p/tesseract-ocr/downloads/detail?name=eng.traineddata.gz
```
unzip it (gzip -d eng.traineddata.gz) and copy to /usr/local/share/tessdata.
```
- remember that you must have tesseract header files in /usr/local/include , this is IMPORTANT!

2. Clone or download this [**repository**](https://github.com/k0staa/build-opencv-for-android) and follow the steps from README.md. 

3. If everythig goes smooth you should have your binaries compiled. Best luck!



### License
Please read OpenCV license in LICENSE file.

