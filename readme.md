# American Sign Language Recognition Using CNN

## What I did here
1. The first thing I did was, I created 26 gesture samples using OpenCV. For each gesture I captured 1200 images which were 50x50 pixels. All theses images were in grayscale which is stored in the gestures/ folder. Due to the large sized getures/ folder, I didnot upload it to GitHub. Click <a href="https://drive.google.com/drive/folders/1kipCgJw51qj5Pm9VQsgvtbmh6zvSDXV6?usp=sharing">here</a> for the gestures. The pictures were flipped using flip_images.py. This script flips every image along the vertical axis. Hence each gesture has 2400 images.
2. Learned what a CNN is and how it works. Best resources were <a href="https://www.tensorflow.org/get_started/">Tensorflow's official website</a> and <a href="https://machinelearningmastery.com">machinelearningmastery.com</a>.
3. Created a CNN which look a lot similar to <a href="https://www.tensorflow.org/tutorials/layers">this MNIST classifying model</a> using both Tensorflow and Keras. If you want to add more gestures you might need to add your own layers and also tweak some parameters, that you have to do on your own.
4. Then used the model which was trained using Keras on a video stream.
5. As of today, I have stored the 26 gestures which are alphabets from A-Z. And trained the model on these images.

There are a lot of details that I left. But these are the basic and main steps.

## Requirements
0. Python 3.7
1. <a href="https://tensorflow.org">Tensorflow 2.7</a>
2. <a href="https://keras.io">Keras 2.7</a>
3. OpenCV 4.5.4.60
4. h5py
5. pyttsx3
6. PyQt5
7. A good grasp over the above 5 topics along with neural networks. Refer to the internet if you have problems with those. I myself am just a begineer in those.
8. A good CPU (preferably with a GPU).

## Installing the requirements
1. Start your terminal of cmd depending on your os.
  2. If you have a NVidia GPU then make sure you have the prerequisites for Tensorflow GPU installation (Refer to official site). Then use this commmand

    pip install -r requirements_gpu.txt

  3. In case you do not have a GPU then use this command

    pip install -r requirements_cpu.txt

## How to use this repo
I have made a GUI for setting up histogram, recognizing single gesture and wording those characters and converting them to speech.

### Creating a gesture 
  1. First set your hand histogram. You do not need to do it again if you have already done it. But you do need to do it if the lighting conditions change. To do so type the command given below and follow the instructions below.
    
    python 5_set_hand_hist.py

  * A windows "Set hand histogram" will appear.
  * "Set hand histogram" will have 50 squares (5x10).
  * Put your hand in those squares. Make sure your hand covers all the squares.
  * Press 'c'. 1 other window will appear "Thresh".
  * On pressing 'c' only white patches corresponding to the parts of the image which has your skin color should appear on the "Thresh" window. 
  * Make sure all the squares are covered by your hand.
  * In case you are not successful then move your hand a little bit and press 'c' again. Repeat this until you get a good histogram.
  * After you get a good histogram press 's' to save the histogram. All the windows close.
  
  2. I already have added 26 (A-Z) gestures. It is on you if you want to add even more gestures or replace my gestures. Hence this step is <b>OPTIONAL</b>. To create your own gestures or replace my gestures do the following. It is done by the command given below. On starting executing this program, you will have to enter the gesture number and gesture name/text. Then an OpenCV window called "Capturing gestures" which will appear. In the webcam feed you will see a green window (inside which you will have to do your gesture) and a counter that counts the number of pictures stored.

    python extra1_create_gestures.py   

  3. Press 'c' when you are ready with your gesture. Capturing gesture will begin after a few seconds. Move your hand a little bit here and there. You can pause capturing by pressing 'c' and resume it by pressing 'c'. Capturing resumes after a few secondAfter the counter reaches 1200 the window will close automatically.

  After capturing all the gestures you can flip the images using

    python extra2_flip_images.py

  4. When you are done adding new gestures run the load_images.py file once. You do not need to run this file again until and unless you add a new gesture.
    
    python 2_load_images.py

### Displaying all gestures
  1. To see all the gestures that are stored in 'gestures/' folder run this command
    
    python 1_display_all_gestures.py

### Training a model
  1. So training can be done with Keras.

    python 3_cnn_keras.py
2. If you use Keras you will have the model in the root directory by the name cnn_model_keras.h5.

You do not need to retrain your model every time. In case you added or removed a gesture then you need to retrain it.

### Get model reports
  1. To get the classification reports about the model make sure you have test_images and test_labels file which are generated by 2_load_images.py. In case you do not have them run 2_load_images.py file again. Then run this file

    python 4_get_model_reports.py
  2. You will get the confusion matrix, f scores, precision and recall for the predictions by the model.

### Testing gestures
I ended up using Keras' model, as the loading the model into memory and using it for prediction is super easy.
   1. First set your hand histogram. 0. Watch the video guide for setting the hand histogram <a href='https://youtu.be/KYfBLeYDMW4'>here</a>. You do not need to do it again if you have already done it. But you do need to do it if the lighting conditions change. To do so type the command given below and follow the instructions below.
    
    python 5_set_hand_hist.py

  * A windows "Set hand histogram" will appear.
  * "Set hand histogram" will have 50 squares (5x10).
  * Put your hand in those squares. Make sure your hand covers all the squares.
  * Press 'c'. 1 other window will appear "Thresh".
  * On pressing 'c' only white patches corresponding to the parts of the image which has your skin color should appear on the "Thresh" window. 
  * Make sure all the squares are covered by your hand.
  * In case you are not successful then move your hand a little bit and press 'c' again. Repeat this until you get a good histogram.
  * After you get a good histogram press 's' to save the histogram. All the windows close.
  2. For recognition start the recognize_gesture.py file.

    python 6_recognize_gesture.py
3. You will have a small green box inside which you need to do your gestures.

### Using 7_text_speech_and_wording.py
Here is where you will have all the fun. 
  1. First set your hand histogram. You do not need to do it again if you have already done it. But you do need to do it if the lighting conditions change. To do so type the command given below and follow the instructions below.
    
    python 5_set_hand_hist.py

  * A windows "Set hand histogram" will appear.
  * "Set hand histogram" will have 50 squares (5x10).
  * Put your hand in those squares.
  * Press 'c'. 2 other windows will appear. "res" and "Thresh".
  * On pressing 'c' only the parts of the image which has your skin color should appear on the "res" window. White patches corresponding to this should appear on the "Thresh" window. 
  * In case you are not successful then move your hand a little bit and press 'c' again. Repeat this until you get a good histogram.
  * After you get a good histogram press 's' to save the histogram. All the windows close.
  
  2. Start the file.
  
    python 7_text_speech_and_wording.py

#### Text Mode
1. In text mode you can create your own words using fingerspellings or use the predefined gestures.
2. The text on screen will be converted to speech on removing your hand from the green box
3. Make sure you keep the same gesture on the green box for 15 frames or else the gesture will not be converted to text.