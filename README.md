# yolov7-face


| Method           |  Test Size | Easy  | Medium | Hard  | Link  |
| -----------------| ---------- | ----- | ------ | ----- | ----- |
| yolov7-tiny-leak | 640        | 93.2  | 91.3   | 83.0  | [google](https://drive.google.com/file/d/1B2F5YuERfMEfJeRXfz5oMxI8wcZLmvFJ/view?usp=sharing) |
| yolov5s          | 640        | 94.0  | 92.1   | 84.5  | [google](https://drive.google.com/file/d/1V7BMMTRk89YzoPHTw6qW3KSOwU_rlBGq/view?usp=sharing) |
| yolov7-lite-e    | 640        | 91.1  | 87.5   | 70.9  | [google](https://drive.google.com/file/d/192NLp3tu3nF7lHq62twH6Vgl_ixGfjrY/view?usp=sharing) |

### Demo

Download the model place into `weights` folder, then run:

```
python detect.py --weights weights/yolov7-tiny-face.pt --view-img
```

### Deploy

事实上这个仓库主要是验证wnnx在复杂模型下的推理能力，当然这当中存在着非常多的坑，最终，我们可以做到NCNN里面做不到的东西，后处理几乎全部融合在模型里面，外部只需要做一个score判断即可。

wnnx的推理结果：

![](https://raw.githubusercontent.com/jinfagang/public_images/master/20221111191658.png)

![](https://raw.githubusercontent.com/jinfagang/public_images/master/20221111191719.png)

![](https://raw.githubusercontent.com/jinfagang/public_images/master/20221111191731.png)

第一张图为yolov7-tiny，后面两张图为 yolov7-lite-e，单线程在CPU下跑的realtime，多线程更快，fp16更快，精度还可以。




### Export

export to onnx and torchscript:

```
python export.py --weights weights/yolov7-tiny-face.pt
```


#### Dataset

[WiderFace](http://shuoyang1213.me/WIDERFACE/)

[yolov7-face-label](https://drive.google.com/file/d/1FsZ0ACah386yUufi0E_PVsRW_0VtZ1bd/view?usp=sharing)

#### Test

![](data/images/result.jpg)


#### Demo

* [ncnn_Android_face](https://github.com/FeiGeChuanShu/ncnn_Android_face)

#### References

* [https://github.com/deepcam-cn/yolov5-face](https://github.com/deepcam-cn/yolov5-face)

* [https://github.com/WongKinYiu/yolov7](https://github.com/WongKinYiu/yolov7)

* [https://github.com/TexasInstruments/edgeai-yolov5/tree/yolo-pose](https://github.com/TexasInstruments/edgeai-yolov5/tree/yolo-pose)

* [https://github.com/ppogg/YOLOv5-Lite](https://github.com/ppogg/YOLOv5-Lite)
