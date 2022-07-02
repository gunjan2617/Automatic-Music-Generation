# Automatic Music Generation
In Automatic Music Generation a system composes short pieces of music using different parameters like pitch interval, notes, chords, tempo, etc. In this Project we have used Piano Instrument.

## Introduction:
An Automatic Music Generation model is created using Long Short Term Memory(LSTM). LSTM is a form of RNN (Recurrent Neural Network) that can solve problems that RNNs can't. The Long-Term Dependency Problem of RNNs is solved by LSTM, which means that RNN networks maintain data from past output in memory for a relatively short time. LSTM also addresses the Vanishing Gradient problem, in which the model tries to minimise loss after each time step by computing loss with regard to particular weights in order to reach the optimum result. After a particular amount of time, this weight approaches 0 or disappears entirely, and the model ceases to train.

## LSTM Model:
LSTMs deal with both Long Term Memory (LTM) and Short Term Memory (STM) and for making the calculations simple and effective it uses the concept of gates.
* **Forget Gate:** LTM goes to forget gate and it forgets information that is not useful.
* **Learn Gate:** Event(current input) and STM are combined together containing information that is recently learnt and forgetting any unnecessary information.
* **Remember Gate:** LTM information that hasn't been forgotten and the STM and Event are combined together in Remember gate which outputs a new updated LTM.
* **Use Gate:** This gate also uses information from LTM, STM, and Event to predict the output of a newly updated STM.

<img src = "https://user-images.githubusercontent.com/88222317/176985574-f66a9c43-1807-42f4-b8a3-5de71202047b.png" width="600" height="300" />

Image Source: Udacity

## Methodology:
### Libraris Used:
* music21: Python library used to parse and read various musical files. Here, Musical Instrument Digital Interface(MIDI) files have been used.
* Tensorflow 2.2: Open-source library for Machine Learning and AI.
* Sklearn: Library for Machine Learning algorithms.
* NumPy: For arrays
* Matplotlib: For plotting graphs

### Datset Used:
The dataset used consists of Classical Piano MIDI files containing compositions of 19 famous composers from [Classical Piano MIDI Page](http://www.piano-midi.de/).

### How to code:
#### Read the MIDI file:
* Import the required libraries.
* Call each MIDI file from its directory and parse the file.
* Obtain the data only for piano instrument, seperating all other instruments.
* Iterate over all the parts of sub stream elements to check if element's type is Note or Chord. If it is Chord, split them into notes.
* Collect all the notes in an array.

#### Input and Output Sequences for the Model:
* Identify the Unique Notes and find the frequency of each such note.
* Filter notes wuth threshold frequency greater than 50 Hz.
* Create a dictionary to convert note index to note and vice versa.
* Create the input and output sequences for the model by using a timestep of 50.
* Reshape input and output for the model and split the input into 80% for training and 20% for testing sets.

#### Create the Model and Training the Neural Network:
* Create the model with two stacked LSTM layers with the latent dimension of 256 and a fully connected layer for the output with softmax activation.
* Compile the model using Adam optimizer and train the neural network for 120 epochs.

#### Generating notes from the Trained Model:
* Use the trained model to predic the notes by generating a random index for the input array.
* Use the ‘np.argmax()’ function to get the data of the maximum probability value, which is converted to a note using the dictionary.
* Repeat the process to generate 200 notes.
* Save the final predicted notes as a MIDI file.

### Architecture:
Two stacked LSTM layers have been used with a dropout rate of 0.5. Dropout Layer is a regularization technique to reduce overfitting in deep learning models. A fully connected layer of size equal to the length of unique notes is used with 'softmax' activation(used for multi-class classification problems).

<img src = "https://user-images.githubusercontent.com/88222317/176988415-3867dbdc-5783-4b54-9b05-1d5a0f438c5b.png" width="500" height="350" />

## Results:
### Plot of Accuracy vs Epochs:
<img src = "https://user-images.githubusercontent.com/88222317/176988833-468cae28-01da-4353-a53a-3e7ea5f4307d.png" width="400" height="250" />

## Plot of Loss vs Epochs:
<img src = "https://user-images.githubusercontent.com/88222317/176989355-4b1a7267-06f1-4341-a267-b09af802be16.png" width="400" height="250" />

**Dataset**     | **Accuracy**    | **Loss**
-------------   | -------------   |------------
Training        |  0.8208         | 0.5325
Testing         |  0.5330         | 2.3930 

You can listen to the predicted output music by downloading the MIDI files that have been uploaded above.

## References:
[Udacity: Architecture of LSTM Network](https://auth.udacity.com/sign-in?next=https%3A%2F%2Fclassroom.udacity.com%2Fauthenticated)

[Data Flair Automatic Music Generation using Deep Learning](https://data-flair.training/blogs/automatic-music-generation-lstm-deep-learning/)

