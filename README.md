# ABO-detector
A for Apple, B for Banana, O for Orange. 在mac上用tensorFlow的model训练苹果、香蕉、橘子识别器。

训练环境和方法请看[TensorFlow-Object-Detection-API-Tutorial-Train-Multiple-Objects-On-Macos](https://github.com/davelet/TensorFlow-Object-Detection-API-Tutorial-Train-Multiple-Objects-On-Macos)。

## fruit-imanges目录
abo的图片和标记数据。

train目录是训练图片和标记，test是测试集。

## 工具

- xml_to_csv.py 用于将标记数据装换为csv文件
- generate_tfrecord.py 用于将csv文件转为tfrecord文件
- Object_detection_webcam.py 用于通过摄像头测试

## 训练（使用特定模型）
在object_detection目录下执行
> python model_main.py \
    --pipeline_config_path=/Users/sheldon/pythonProjects/py3venv/kaggle/faster_rcnn_inception_v2_pets.config \
    --model_dir=/Users/sheldon/pythonProjects/py3venv/kaggle/fruit-images \
    --alsologtostderr

## 导出图
在object_detection目录下执行
> python export_inference_graph.py --input_type image_tensor --pipeline_config_path /Users/sheldon/pythonProjects/py3venv/kaggle/faster_rcnn_inception_v2_pets.config --trained_checkpoint_prefix /Users/sheldon/pythonProjects/py3venv/kaggle/fruit-images/model.ckpt-2132 --output_directory /Users/sheldon/pythonProjects/py3venv/kaggle/fruit-images/graph

## 测试
在object_detection目录下执行
> python /Users/sheldon/pythonProjects/ABO-detector/Object_detection_webcam.py

## 官方资料

[TensorFlow lite Object detection](https://www.tensorflow.org/lite/models/object_detection/overview)

[对象识别](https://www.tensorflow.org/lite/models/object_detection/overview#customize_model)

[图片分类](https://www.tensorflow.org/lite/models/image_classification/overview)

[模型转到移动端](https://www.tensorflow.org/lite/convert/python_api)

https://github.com/nnsuite/nnstreamer/wiki/%5BTF-Lite%5D-How-to-Convert-Tensorflow-Model-to-TF-Lite-Model

https://www.quantumobile.com/mobile-object-detector-with-tensorflow-lite/
