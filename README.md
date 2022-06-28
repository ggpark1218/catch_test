# catch_test
## [Advanced Flutter 캠프 1주차 - tflite custom model 만들기]

custom model을 만들기 위해서는 csv 파일이 필요하다. 이 csv 파일에는 각 사진의 좌표 정보가 저장되어있다. 저번 방학 때랑 학기 중 모두 구글 클라우드 플랫폼으로 시도를 해보았지만 csv파일에 정보가 모델 메이커와 연동이 되지 않았다. 그래서 새로운 방법을 시도해보았지만 여전히 어려웠다. 플러터로 모델 메이커로 만든 모델을 적용하는게 튜토리얼이 없다… 그래도 해보자!

## tflite model maker 사용하기

---

[tflite_model_maker.object_detector.DataLoader | TensorFlow Lite](https://www.tensorflow.org/lite/api_docs/python/tflite_model_maker/object_detector/DataLoader#from_csv)

[TFLite Model Maker Object Detection](https://youtu.be/qukBhHIJh-k)

[GitHub - TannerGilbert/TFLite-Object-Detection-with-TFLite-Model-Maker: Custom object detection with the TFLite Model Maker](https://github.com/TannerGilbert/TFLite-Object-Detection-with-TFLite-Model-Maker)

[Object Detection with TensorFlow Lite Model Maker](https://www.tensorflow.org/lite/models/modify/model_maker/object_detection)

### cache로 부터  데이터 로드

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a3caa477-e53a-4cda-8752-1e824bd6f581/Untitled.png)

### csv로 부터 데이터 로드

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9bcef103-f54f-4867-80ae-270f82d1a1dc/Untitled.png)

[Formatting a training data CSV | AutoML Vision Object Detection | Google Cloud](https://cloud.google.com/vision/automl/object-detection/docs/csv-format)

[Quickstart: Label images by using the AutoML Vision Edge API | AutoML Vision Object Detection | Google Cloud](https://cloud.google.com/vision/automl/object-detection/docs/label-images-edge-model#preparing_a_dataset)

training data set을 csv로 만들기 위해서는 google cloud platform 에 AutoML Vision을 사용한다.

→이거 자꾸 구글 클라우드 플랫폼 버킷에 있는 csv가 모델 메이커와 연결이 안됨

### **pascal_voc로 부터 데이터셋 로드**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5bfccdf9-c212-4896-a143-14b029524fc0/Untitled.png)

[COCO data format for Object detection](https://towardsdatascience.com/coco-data-format-for-object-detection-a4c5eaf518c5)

[GitHub - tzutalin/labelImg: 🖍️ LabelImg is a graphical image annotation tool and label object bounding boxes in images](https://github.com/tzutalin/labelImg)

<aside>
💡 이 영상에서는 이 방법을 채택

</aside>

1. 마이크로 컨트롤러를 감지하는 이미지 데이터셋 준비

[Microcontroller Detection](https://www.kaggle.com/datasets/tannergi/microcontroller-detection/code)

1. labelImg 를 이용해 이미지 라벨링

[Tensorflow Object Detection with Tensoflow 1 - Create your own object detector](https://youtu.be/HjiBbChYRDw)

[Tensorflow Object Detection with Tensorflow 2: Creating a custom model](https://gilberttanner.com/blog/tensorflow-object-detection-with-tensorflow-2-creating-a-custom-model/)

1. xml → csv

[https://github.com/datitran/raccoon_dataset.git](https://github.com/datitran/raccoon_dataset.git)

![스크린샷 2022-06-24 오후 1.53.06.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2f0e8279-ea33-444c-8a33-5269ee1380e3/스크린샷_2022-06-24_오후_1.53.06.png)

[Tensorflow Object Detection with Tensoflow 1 - Create your own object detector](https://youtu.be/HjiBbChYRDw)

10:03초

![스크린샷 2022-06-24 오후 1.57.04.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9e31275b-c3df-4aa1-b0dd-7b646e70338d/스크린샷_2022-06-24_오후_1.57.04.png)

1) xml_to_csv.py를 실행해서 xml→csv로 변환

2) generate_tfcord.py에서 라벨이름 custom했던 라벨 이름으로 변환

3) lablemap file 만들기

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d949b8ce-a259-445d-ad31-b1790043acd3/Untitled.png)

4)config 파일 설정

→유튜브 더 참고

[COCO data format for Object detection](https://towardsdatascience.com/coco-data-format-for-object-detection-a4c5eaf518c5)

1. 모델 메이커를 사용해 이미지 감지 모델 만들기

[https://github.com/TannerGilbert/TFLite-Object-Detection-with-TFLite-Model-Maker.git](https://github.com/TannerGilbert/TFLite-Object-Detection-with-TFLite-Model-Maker.git)

[Google Colaboratory](https://colab.research.google.com/github/TannerGilbert/TFLite-Object-Detection-with-TFLite-Model-Maker/blob/master/Train_custom_object_detector_with_TFLite_Model_Maker.ipynb)

1. 안드로이드 용으로 배포

[https://github.com/googlecodelabs/odml-pathways](https://github.com/googlecodelabs/odml-pathways)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9f22f62c-52b4-4284-9c31-4d286195c029/Untitled.png)

[Build and deploy a custom object detection model with TensorFlow Lite (Android) | Google Developers](https://developers.google.com/codelabs/tflite-object-detection-android#4)

1. flutter에 모델 적용

찾아봐야함

## pytorch + flutter 찾아보기

[How to use Pytorch mobile on Flutter](https://dev.to/ramgendeploy/how-to-use-pytorch-mobile-on-flutter-1827)

[Google Colaboratory](https://colab.research.google.com/drive/1IHpT1Cv17bJVleWBEyRifGJiPyFFVv0o?usp=sharing#scrollTo=Das7YGgqmSUL)

[yolov4-tflite-CUSTOM-android-app/Mobile_Object_Detection.ipynb at main · skykongkong8/yolov4-tflite-CUSTOM-android-app](https://github.com/skykongkong8/yolov4-tflite-CUSTOM-android-app/blob/main/Mobile_Object_Detection.ipynb)

labelImg (yolo 모델의 csv를 만들수 있는 툴)

- > python코드로 training test set을 만들 수 있고
- > python코드로 모델로 추출
- > yolo모델을 만들고
- > flutter에서 yolo를 적용

[Vehicles-OpenImages Object Detection Dataset - 416x416](https://public.roboflow.com/object-detection/vehicles-openimages/1)

---

나머지 그냥 참고 링크

[https://github.com/yaashwardhan/On-Device-Machine-Learning-App-TensorfowLite-and-Flutter](https://github.com/yaashwardhan/On-Device-Machine-Learning-App-TensorfowLite-and-Flutter)

[On Device Machine Learning: Train And Run TensorFlow Lite Models In Your Flutter Apps](https://medium.com/google-cloud/on-device-machine-learning-train-and-run-tensorflow-lite-models-in-your-flutter-apps-15ea796e5ad4)

[How to Train a Custom Mobile Object Detection Model (with YOLOv4 Tiny and TensorFlow Lite)](https://blog.roboflow.com/how-to-train-a-custom-mobile-object-detection-model/)

[[10]Android Yolo detection 구현하기](https://sj-d.tistory.com/17)

[Custom Object Detection with TensorFlow YOLOv4, and TFLite | Windows, Linux | Image, Video](https://youtu.be/vzTCJM18uoM)

[.pt 파일에서 .tflite로 어떻게 변환하는지 궁금합니다. - 인프런 | 질문 & 답변](https://www.inflearn.com/questions/315531)

[How to Train A Custom Object Detection Model with YOLO v5](https://towardsdatascience.com/how-to-train-a-custom-object-detection-model-with-yolo-v5-917e9ce13208)

[GitHub - ultralytics/yolov5: YOLOv5 🚀 in PyTorch > ONNX > CoreML > TFLite](https://github.com/ultralytics/yolov5#tutorials)
