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

<img src = "" width="800" height="350" />

Image Source: Udacity

## Methodology:
### Libraris Used:
* music21: Python library used to parse and read various musical files. Here, Musical Instrument Digital Interface(MIDI) files have been used.
* Tensorflow 2.2: Open-source library for Machine Learning and AI.
* Sklearn: Library for Machine Learning algorithms.
* NumPy: For arrays
* Matplotlib: For plotting graphs

### Datset Used:
The dataset used consists of Classical Piano MIDI files containing compositions of 19 famous composers from [Classical Piano MIDI Page]http://www.piano-midi.de/.
