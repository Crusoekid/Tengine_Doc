# **转换**

## **转换指令**
* Caffe

```bash
./install/bin/tm_convert_tool -f caffe -p mobilenet_deploy.prototxt -m mobilenet.caffemodel -o mobilenet.tmfile
```

* MxNet

```bash
./install/bin/tm_convert_tool -f mxnet -p mobilenet1_0-symbol.json -m mobilene1_0-0000.params -o mobileent.tmfile
```

* ONNX

```bash
./install/bin/tm_convert_tool -f onnx -m mobilenet.onnx -o mobilenet.tmfile
```

* TensorFlow

```bash
./install/bin/tm_convert_tool -f tensorflow -m mobielenet_v1_1.0_224_frozen.pb -o mobilenet.tmfile
```

* TFLITE

```bash
./install/bin/tm_convert_tool -f tflite -m mobielenet.tflite -o mobilenet.tmfile
```

* DarkNet: darknet only support for yolov3 model

```bash
./install/bin/tm_convert_tool -f darknet -p yolov3.cfg -m yolov3.weights -o yolov3.tmfile
```

* NCNN

```bash
./install/bin/tm_convert_tool -f ncnn -p mobilenet.params -m mobilenet.bin -o mobilenet.tmfile
```

* MegEngine

```bash
./install/bin/tm_convert_tool -f megengine -m mobilenet.pkl -o mobilenet.tmfile
```