---
layout: post
title:  "Convolution in Caffe"
date:   2016-11-22 20:21:12 +0800
categories: Deep-Learning Caffe
---
The implementation of convolution in Caffe use the matrix multiplication indeed. As described in its official website: “The Caffe strategy for convolution is to reduce the problem to matrix-matrix multiplication. This linear algebra computation is highly-tuned in BLAS libraries and efficiently computed on GPU devices.”[1]. Below is detailed info:
<img width="100" src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_medias/img/caffe_conv_1.jpg"></br>
<img width="100" src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_medias/img/caffe_conv_2.jpg"></br>
<img width="100" src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_medias/img/caffe_conv_3.jpg"></br>
<img width="100" src="https://raw.githubusercontent.com/xymeng16/xymeng16.github.io/master/_medias/img/caffe_conv_4.jpg"></br>
(those slides belongs to the creator of the Caffe: Yangqing Jia)

In Caffe, convolution is included in those files mainly: src/caffe/layers/conv_layer.cu, src/caffe/layers/base_conv_layer.cpp, src/caffe/util/math_functions.cu, src/caffe/util/in2cool.cu.
