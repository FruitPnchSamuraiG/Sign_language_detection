# Sign-Language-Recognition-Using-LSTM

## General

After the start of the pandemic the use of E-Learning has increased drastically. By 2026 the E-learning industry is seat to reach at least $400 billion. With the rise of this new fashion of education no child should be left behind. Children with the disability of hearing loss are held at a disadvantage due to the reason that they have a hard time hearing the lectures that are present on the screen. Other factors would be a mute child who would not be able to speak in according to the response of the lecturer. In order for these children to cope with education the American Sign Language was created not only to help them with education but to provide ease for their daily lives. To help these children with their education we proposed a model that will help the student make ASL gestures to the camera and have it read and provide feedback on what language was read. For this we used OpenCV with Mediapipe Holistic to identify the key markers of the poser with all the values to be collected and then be trained on the Long Short Term Memory Architecture. 

## MediaPipe Holistic
The initial step of the program is to identify the Keypoints of the user. MP Holistic is an API created by Mediapipe which identifies the keypoints on a body by identifying the holistic key points

`mp_holistic = mp.solutions.holistic
mp_drawing = mp.solutions.drawing_utils`

These two api calls, are calls the Holistic API uses to identify the keypoints holistic keypoints and draw it



The function
`draw_landmarks(image, results)`

Draws landmarks of the identified keypoints on the user



However wth a few extra lines of code 
`draw_styled_landmarks(image,results)`

The keypoints can be color coded for the viewer to identify the different parts of the human




## Collecting the Data
After the mediapipe has been defined the keypoints must be collected and stored to be trained on later. 

`def extract_keypoints(results)` 

This takes in the extracted keypoints from the video and concatenated the values into a numpy array.


The collected data is abeled as 'Hello', 'Thanks', and 'I Love You'. In order to collect the data the user poses for the three different action in for 30 sequences for 30 frames. For a total of 90 collectd sequences

The identified keypoints are stored in the folder called MP_Data, with each sequence in its respective action folder in the .npy format 


## Training the Long Short Term Memory
To train the Long Short Term Memory the model selected was a Sequential model trained on 3 layers and 2 dense layers. Since it is catagorical data the model was compiled as:

`model.compile(optimizer = 'Adam',loss='categorical_crossentropy',metrics=['categorical_accuracy'])`

The model was then Trained on 2000 epochs.

## Testing in Real time
These are the testing results in real time from the project after training the data on the LSTM Architecture using MP Holistic

![Screenshot 2023-11-07 195457](https://github.com/FruitPnchSamuraiG/Sign_language_detection/assets/146465657/7ed6601d-2cf0-451b-9760-06c89ef6d065)


#### 1.  Color Coded Probability Viewer

- This is a probability bar which shows the gesture that is being identified the most in the test. The bar rises with the gesture it recognizes most. The color for each bar is as follows:

  - Blue/Hello
  - Green/Thanks
  - Orange/I Love You
  - Purple/ Rashford celebration


## Run
### Run on Old Weights
To run on the previous versions weights the user has to run load.weights("my_model_new.h5")

      - When the camera opens pose in the Sign Language poses for 30 sequences in 'Hello', 'Thanks', and 'I Love You'.

## Output
![Screenshot 2023-11-07 195749](https://github.com/FruitPnchSamuraiG/Sign_language_detection/assets/146465657/555df70b-4efc-4f8b-af50-be5d65d24451)


