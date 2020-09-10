# CarEstimation  

## Overview  
You can get an automatic quote for your car.  
The total amount will change when you select an option.  
## Description
I created an app using Vue.js because I wanted to challenge the frameworks other than Rails that I had studied so far. 
The content of the app is created with reference to the 86 estimation simulator, which is my car.

## Demo  
![サンプル1](car.gif)
![サンプル2](car2.gif)
## Installation  
```
$ git clone https://github.com/Belfraw/car_estimation.git
$ cd car_estimation
$ npm run serve
```
## Anything Else
The image is set to switch when white is selected in the color selection. 
I was a little worried about how to display it with v-if because the additional option fee is set in v-model.

The problem is that when switching between the instrument panel image and the sheet image,
the previously selected image remains, so I want to be able to switch it well.

## Deploy
