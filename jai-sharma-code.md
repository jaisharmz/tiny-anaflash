# Jai Sharma Code and Explanations

## 19 January 2024
The goal was to reproduce the tinyML benchmark for image classification. We can do this by either running the testing metrics on the pretrained model weights or training a new model ourselves and finding the metrics on that model. 

First, clone this respository by using the following command:
```
git clone https://github.com/jaisharmz/tiny-anaflash.git
```

Then, run a few setup commands:
```
cd ./benchmark/training/image_classification # go into the image classification directory
pip3 install -r requirements.txt # install required packages
wget https://www.cs.toronto.edu/~kriz/cifar-10-python.tar.gz # download data
tar -xvf cifar-10-python.tar.gz # unpack zipped data
python3 perf_samples_loader.py # split data into batches
```

After cloning the repository, we can run the commands below to print the metrics of the pretrained model before and after quantization. 
```
python3 test.py # find benchmark results on model before quantization
python3 tflite_test.py # find benchmark results on model after quantization
```
If you would like to train and test a model from scratch, run the following commands.
```
python3 train.py # collect data and train model from scratch (changed from 500 epochs to 5 epochs to limit training time)
python3 test.py # find benchmark results on trained model before quantization
python3 model_converter.py # quantize trained model
python3 tflite_test.py # find benchmark results on trained model after quantization
```
If run in sequence, these commands should work as intended. However, to manually set the path to the `.h5` or `.tflite` weights file of the model that is to be tested, go to the `benchmark/training/image_classification/keras_model.py` file and modify the `get_model_name()` function (if not yet quantized) or the `get_quant_model_name()` function (if the model has been quantized) to return the weights path of the model. 
