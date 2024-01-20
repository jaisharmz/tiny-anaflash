# Jai Sharma Code and Explanations - Anaflash Inc.

## 19 January 2024
The goal was to reproduce the tinyML benchmark for image classification. We can do this by either running the testing metrics on the pretrained model weights or training a new model ourselves and finding the metrics on that model. 

First, clone this respository by using the following command:
```
git clone https://github.com/jaisharmz/tiny-anaflash.git
```

After cloning the repository, we can run the commands below to print the metrics of the pretrained model before and after quantization. 
```
python3 ./benchmark/training/image_classification/test.py # find benchmark results on model before quantization
python3 ./benchmark/training/image_classification/tflite_test.py # find benchmark results on model after quantization
```
If you would like to train and test a model from scratch, run the following commands.
```
python3 ./benchmark/training/image_classification/train.py # collect data and train model from scratch
python3 ./benchmark/training/image_classification/test.py # find benchmark results on trained model before quantization
python3 ./benchmark/training/image_classification/model_converter.py # quantize trained model
python3 ./benchmark/training/image_classification/tflite_test.py # find benchmark results on trained model after quantization
```
If run in sequence, these commands should work as intended. However, to manually set the path to the `.h5` or `.tflite` weights file of the model that is to be tested, go to the `benchmark/training/image_classification/keras_model.py` file and modify the `get_model_name()` function (if not yet quantized) or the `get_quant_model_name()` function (if the model has been quantized) to return the weights path of the model. 
