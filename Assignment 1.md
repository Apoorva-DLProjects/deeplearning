**What are Channels and Kernels (according to EVA)?**

Channels represent the number of layers (Features) that represent the data. For example: Image represented as RGB has 3 channels.
Kernels (Feature Extractor) are used to detect image features by convolving across the image. During convolution with a part of image, each element of the image is added to its local neighbours, weighted by the kernel. For Image of Size YxY, applying 3x3 Kernel yields (Y-2)*(Y-2) size 

![Convolution](https://upload.wikimedia.org/wikipedia/commons/1/19/2D_Convolution_Animation.gif)

**Why should we (nearly) always use 3x3 kernels?**

1. 3x3 convolution is commonly used filter having 9 parameters. It allows for same receptive field with least parameters. 
1. Odd filters are preferred because if we were to consider the final output pixel (of next layer) that was obtained by convolving on the previous layer pixels, all the previous layer pixels would be symmetrically around the output pixel. Without this symmetry, we will have to account for distortions across the layers. Therefore, even sized kernel filters aren’t preferred.
1. The features that would be extracted using 3x3 Kernel will be highly local and may not have a more general overview of the image. This helps capture smaller, complex features in the image. 
1. For same global receptive field of 5x5, we apply 3x3 kernel twice to get a final value, we actually used (3x3 + 3x3) weights instead of (5x5) weigths. So, with smaller kernel sizes, we get lower number of weights and more number of layers. 
1. Due to the lower number of weights, this is computationally efficient. 
1. Current GPUs are optimized for 3x3 kernels and all larger kernels are internally broken down to 3x3 for faster computation.


**How many times to we need to perform 3x3 convolutions operations to reach close to 1x1 from 199x199 (type each layer output like 199x199 > 197x197...)**

3x3 Kernel reduces the image size by 2 for every convolution operation. To reduce 199x199 size Image to 1x1 image, the number of convolution required is 199/2 = 99
1. Input:199x199 - (3x3 Kernel Convolution) -> Output:197x197
1. Input:197x197 - (3x3 Kernel Convolution) -> Output:195x195
1. Input:195x195 - (3x3 Kernel Convolution) -> Output:193x193
1. Input:193x193 - (3x3 Kernel Convolution) -> Output:191x191
1. Input:191x191 - (3x3 Kernel Convolution) -> Output:189x189
1. Input:189x189 - (3x3 Kernel Convolution) -> Output:187x187
1. Input:187x187 - (3x3 Kernel Convolution) -> Output:185x185
1. Input:185x185 - (3x3 Kernel Convolution) -> Output:183x183
1. Input:183x183 - (3x3 Kernel Convolution) -> Output:181x181
1. Input:181x181 - (3x3 Kernel Convolution) -> Output:179x179
1. Input:179x179 - (3x3 Kernel Convolution) -> Output:177x177
1. Input:177x177 - (3x3 Kernel Convolution) -> Output:175x175
1. Input:175x175 - (3x3 Kernel Convolution) -> Output:173x173
1. Input:173x173 - (3x3 Kernel Convolution) -> Output:171x171
1. Input:171x171 - (3x3 Kernel Convolution) -> Output:169x169
1. Input:169x169 - (3x3 Kernel Convolution) -> Output:167x167
1. Input:167x167 - (3x3 Kernel Convolution) -> Output:165x165
1. Input:165x165 - (3x3 Kernel Convolution) -> Output:163x163
1. Input:163x163 - (3x3 Kernel Convolution) -> Output:161x161
1. Input:161x161 - (3x3 Kernel Convolution) -> Output:159x159
1. Input:159x159 - (3x3 Kernel Convolution) -> Output:157x157
1. Input:157x157 - (3x3 Kernel Convolution) -> Output:155x155
1. Input:155x155 - (3x3 Kernel Convolution) -> Output:153x153
1. Input:153x153 - (3x3 Kernel Convolution) -> Output:151x151
1. Input:151x151 - (3x3 Kernel Convolution) -> Output:149x149
1. Input:149x149 - (3x3 Kernel Convolution) -> Output:147x147
1. Input:147x147 - (3x3 Kernel Convolution) -> Output:145x145
1. Input:145x145 - (3x3 Kernel Convolution) -> Output:143x143
1. Input:143x143 - (3x3 Kernel Convolution) -> Output:141x141
1. Input:141x141 - (3x3 Kernel Convolution) -> Output:139x139
1. Input:139x139 - (3x3 Kernel Convolution) -> Output:137x137
1. Input:137x137 - (3x3 Kernel Convolution) -> Output:135x135
1. Input:135x135 - (3x3 Kernel Convolution) -> Output:133x133
1. Input:133x133 - (3x3 Kernel Convolution) -> Output:131x131
1. Input:131x131 - (3x3 Kernel Convolution) -> Output:129x129
1. Input:129x129 - (3x3 Kernel Convolution) -> Output:127x127
1. Input:127x127 - (3x3 Kernel Convolution) -> Output:125x125
1. Input:125x125 - (3x3 Kernel Convolution) -> Output:123x123
1. Input:123x123 - (3x3 Kernel Convolution) -> Output:121x121
1. Input:121x121 - (3x3 Kernel Convolution) -> Output:119x119
1. Input:119x119 - (3x3 Kernel Convolution) -> Output:117x117
1. Input:117x117 - (3x3 Kernel Convolution) -> Output:115x115
1. Input:115x115 - (3x3 Kernel Convolution) -> Output:113x113
1. Input:113x113 - (3x3 Kernel Convolution) -> Output:111x111
1. Input:111x111 - (3x3 Kernel Convolution) -> Output:109x109
1. Input:109x109 - (3x3 Kernel Convolution) -> Output:107x107
1. Input:107x107 - (3x3 Kernel Convolution) -> Output:105x105
1. Input:105x105 - (3x3 Kernel Convolution) -> Output:103x103
1. Input:103x103 - (3x3 Kernel Convolution) -> Output:101x101
1. Input:101x101 - (3x3 Kernel Convolution) -> Output:99x99
1. Input:99x99 - (3x3 Kernel Convolution) -> Output:97x97
1. Input:97x97 - (3x3 Kernel Convolution) -> Output:95x95
1. Input:95x95 - (3x3 Kernel Convolution) -> Output:93x93
1. Input:93x93 - (3x3 Kernel Convolution) -> Output:91x91
1. Input:91x91 - (3x3 Kernel Convolution) -> Output:89x89
1. Input:89x89 - (3x3 Kernel Convolution) -> Output:87x87
1. Input:87x87 - (3x3 Kernel Convolution) -> Output:85x85
1. Input:85x85 - (3x3 Kernel Convolution) -> Output:83x83
1. Input:83x83 - (3x3 Kernel Convolution) -> Output:81x81
1. Input:81x81 - (3x3 Kernel Convolution) -> Output:79x79
1. Input:79x79 - (3x3 Kernel Convolution) -> Output:77x77
1. Input:77x77 - (3x3 Kernel Convolution) -> Output:75x75
1. Input:75x75 - (3x3 Kernel Convolution) -> Output:73x73
1. Input:73x73 - (3x3 Kernel Convolution) -> Output:71x71
1. Input:71x71 - (3x3 Kernel Convolution) -> Output:69x69
1. Input:69x69 - (3x3 Kernel Convolution) -> Output:67x67
1. Input:67x67 - (3x3 Kernel Convolution) -> Output:65x65
1. Input:65x65 - (3x3 Kernel Convolution) -> Output:63x63
1. Input:63x63 - (3x3 Kernel Convolution) -> Output:61x61
1. Input:61x61 - (3x3 Kernel Convolution) -> Output:59x59
1. Input:59x59 - (3x3 Kernel Convolution) -> Output:57x57
1. Input:57x57 - (3x3 Kernel Convolution) -> Output:55x55
1. Input:55x55 - (3x3 Kernel Convolution) -> Output:53x53
1. Input:53x53 - (3x3 Kernel Convolution) -> Output:51x51
1. Input:51x51 - (3x3 Kernel Convolution) -> Output:49x49
1. Input:49x49 - (3x3 Kernel Convolution) -> Output:47x47
1. Input:47x47 - (3x3 Kernel Convolution) -> Output:45x45
1. Input:45x45 - (3x3 Kernel Convolution) -> Output:43x43
1. Input:43x43 - (3x3 Kernel Convolution) -> Output:41x41
1. Input:41x41 - (3x3 Kernel Convolution) -> Output:39x39
1. Input:39x39 - (3x3 Kernel Convolution) -> Output:37x37
1. Input:37x37 - (3x3 Kernel Convolution) -> Output:35x35
1. Input:35x35 - (3x3 Kernel Convolution) -> Output:33x33
1. Input:33x33 - (3x3 Kernel Convolution) -> Output:31x31
1. Input:31x31 - (3x3 Kernel Convolution) -> Output:29x29
1. Input:29x29 - (3x3 Kernel Convolution) -> Output:27x27
1. Input:27x27 - (3x3 Kernel Convolution) -> Output:25x25
1. Input:25x25 - (3x3 Kernel Convolution) -> Output:23x23
1. Input:23x23 - (3x3 Kernel Convolution) -> Output:21x21
1. Input:21x21 - (3x3 Kernel Convolution) -> Output:19x19
1. Input:19x19 - (3x3 Kernel Convolution) -> Output:17x17
1. Input:17x17 - (3x3 Kernel Convolution) -> Output:15x15
1. Input:15x15 - (3x3 Kernel Convolution) -> Output:13x13
1. Input:13x13 - (3x3 Kernel Convolution) -> Output:11x11
1. Input:11x11 - (3x3 Kernel Convolution) -> Output:9x9
1. Input:9x9 - (3x3 Kernel Convolution) -> Output:7x7
1. Input:7x7 - (3x3 Kernel Convolution) -> Output:5x5
1. Input:5x5 - (3x3 Kernel Convolution) -> Output:3x3
1. Input:3x3 - (3x3 Kernel Convolution) -> Output:1x1
 
**How are kernels initialized?**

The neural network needs to start with some weights and then iteratively update them to better values. Weight and bias initialization for each layer can be set via kernel_initializer and bias_initializer keyword arguments respectively within layers.Dense(). If undefined, default settings of kernel_initializer='glorot_uniform' and bias_initializer='zeros' are applied. 

**What happens during the training of a DNN?**

Using training dataset, DNN Model is trained using training dataset. Kernel weights get updated using back propagation
