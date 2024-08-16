# Cloud-recognition

### This is the data set I used to train my model
https://www.kaggle.com/datasets/nakendraprasathk/cloud-image-classification-dataset/data3

To train the model you need to `cd jetson inference`
Then run the docker 
```
./docker/run.sh --volume /home/nvidia/$PROJECT:/jetson-inference/$PROJECT
```
This is the command for training for the model 
```
python3 train.py --model-dir=/jetson-inference/Cloud-recognition/models/1 /jetson-inference/Cloud-recognition/data/1 --resume=/jetson-inference/Cloud-recognition/models/1/checkpoint.pth.tar 

```

To test the model you can chose and file to use and run this command
```
root@ubuntu:/jetson-inference/Cloud-recognition# python3 classify.py /PATH/TO/FILE
```
Before training it you must set the epochs to however you want, I used 126 epochs but you might need more than that.

To add epochs you need to add this to the end of the command

```
--epochs=NumberOfEpochs
```


Then once youve finished training you must export it by running this command

```
python3 onnx_export.py --model-dir=/jetson-inference/Cloud-recognition/model/1
```
