Jetson_Nano_Class 20200729
==========================

## Jetson Nano

1. Image Net (수업자료 30_ImageNet참고)

< Using the Console Program on Jetson >
```
 Open Terminal
 $ cd jetson-inference/build/aarch64/bin 
 $ ./imagenet-console.py  –-network=googlenet  images/orange_0.jpg   output_0.jpg
 $ ./imagenet-console.py  images/granny_smith_1.jpg   output_1.jpg
```
--network=googlenet은 사용할 CNN의 종류이다
유명한 CNN은 
- ResNet
- VGG16
- VGG19
- Inception_V3
등이 있다.

2. Detect Net (수업자료 31_DetecNet참고)

3. Seg Net  (수업자료 31_DetecNet참고)