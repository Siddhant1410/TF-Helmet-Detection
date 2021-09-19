# TF-Helmet-Detection
A Tensorflow Object detection API based Project that detects the presence and absence of helmet on rider's head.
![alt text](https://raw.githubusercontent.com/Siddhant1410/TF-Helmet-Detection/main/TF-Helmet-Detection/test_results/img1.JPG)

![alt text](https://raw.githubusercontent.com/Siddhant1410/TF-Helmet-Detection/main/TF-Helmet-Detection/test_results/img2.JPG)


# Pre-Requisites:
1. Anaconda Venv
2. Python 3.8 or higher
3. Tensorflow 2.0 
4. Tensorflow GPU support (Optional)
5. Tensorflow Object detection API
6. Protobuf 3.12 or higher

    A detailed guide on how to fulfil these pre-requisites can be found here:
    https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/install.html

After you satisfy the requirements, follow these steps:

# Create the following directories in TF-Helmet-Detection folder:
/models/faster_rcnn_inception_resnet50_v2

/pre-trained-models

/my_model

# Downloading a pre-trained model
1. Move the pipeline.config file from /TF-Helmet-Detection to /models.
2. Browse to the Tensoeflow 2.0 Object Detection Model Zoo: https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/tf2_detection_zoo.md
3. Download 'Faster R-CNN Inception ResNet V2 640x640'. Extract the contents of the file in /pre-trained-models folder.

# Creating test and train records
1. Run the 'xml_to_csv.py' script. You will get 2 files: 'test_labels.csv' and 'train_labels.csv' files in /data folder. 
Copy the 'test_labels.csv' in /data/test folder and 'train_labels.csv' in /data/train folder.
2. Run the 'generate_tfrecord.py' script. You will get 2 files: 'test.record' and 'train.record' in /data folder.
Move these two files to the /annotations folder.

# Configuring the training job:
All the changes have already been made in the pipeline.config file. If you wish, you can change some parameters like, "fine_tune_checkpoint" or "batch_size".
The commands for training, evaluation, model export and tensorboard are given in the 'commands.txt' file. 

1. Start training for the model by executing the training command.
2. In a separate terminal, execute the tensorboard command to monitor the training graph. (Optional)
3. Train your model until the total_loss gradually reduces to < 0.15 ~.
4. Stop the training and execute the evaliation command. Once the command is executes, you shall see the Accuracy scores in the terminal. 
   Close the terminal and reload tensorboard, then head over to images tab to check how your model has performed on the training set.
5. Once the results are satisfactory, execute the export command.
6. Once your model is exported, you should see a new folder called /exported-models. Copy 'my_model' folder from /exported-models and paste it in /TF-Helmet-Detection.
7. Now you can run 'inference_test_model.py' to test how your model works on images outside the dataset. You can add images of your choice in /test_images.
   To run inference on a specific image, open 'inference_test_model.py' and edit: IMAGE_PATHS = 'test_images/<image_of_your_choice.jpg>'





