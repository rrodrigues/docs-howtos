# Opencv Library https://opencv.org/

### build opencv

#### configure

##### basic:
```
cmake -S <projec root folder> -B <build folder>
```

##### slim:
```
cmake -S <projec root folder> -B <build folder> \
    -GNinja \
    -DBUILD_DOCS=OFF \
    -DBUILD_EXAMPLES=OFF \
    -DBUILD_PERF_TESTS=OFF \
    -DBUILD_TESTS=OFF \
    -DBUILD_opencv_apps=OFF \
    -DBUILD_opencv_python2=OFF \
    -DBUILD_opencv_python3=OFF \
    -DBUILD_SHARED_LIBS=ON \
    -DBUILD_opencv_world=YES \
    -DENABLE_CXX11=ON \
    -DCMAKE_CXX_STANDARD=17 
```

##### extra options

* add contrib modules
```
    -DOPENCV_EXTRA_MODULES_PATH=<contrib root folder>/modules \
```

* opengl
```
    -DWITH_OPENGL=YES 
```

* disable module
```
    -DBUILD_opencv_cvv=OFF
```

* macosx options:
```
    -DCMAKE_SKIP_RPATH=YES
```

* build python module:
```    
    -DPYTHON_DEFAULT_EXECUTABLE=`which python3` \
    -DPYTHON3_INCLUDE_DIR=`python3 -c "import sysconfig; print(sysconfig.get_path('platinclude'))"` \
    -DPYTHON3_LIBRARY=`python3 -c "import sysconfig; print(sysconfig.get_path('platlib'))"` \
    -DBUILD_opencv_python2=OFF \
    -DBUILD_opencv_python3=ON \
```

* build with Qt (for ui)
```
    -DWITH_QT=YES \
    -DCMAKE_PREFIX_PATH=<path to qt root folder> \
```

or 

```
    -DQt5Core_DIR=<path to qt root folder>/lib/cmake/Qt5Core \
    -DQt5Gui_DIR=<path to qt root folder>/lib/cmake/Qt5Gui \
    -DQt5Widgets_DIR=<path to qt root folder>/lib/cmake/Qt5Widgets \
    -DQt5OpenGLt_DIR=<path to qt root folder>/lib/cmake/Qt5OpenGL \
    -DQt5Test_DIR=<path to qt root folder>/lib/cmake/Qt5Test \
    -DQt5Concurrent_DIR=<path to qt root folder>/lib/cmake/Qt5Concurrent
```

* extra optios:
```
    -DOPENCV_GENERATE_PKGCONFIG=YES    
```

##### build
```
cmake --build <build folder> --config Release|Debug
```

##### install
```
cmake --install <build dir> --prefix <install dir>
```    

##### iOS

* using cocoapods [from a podspec outside a spec repository](https://guides.cocoapods.org/syntax/podfile.html#pod)

```
pod 'opencv', :podspec => 'https://gist.github.com/rrodrigues/95eac7e162ce7e85aa6a4fb2f7dd2c27'
```


  

