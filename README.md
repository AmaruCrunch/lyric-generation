# Lyrics Generation using MIDI and LSTM

## About the Project

This project focuses on generating lyrics using deep learning models, specifically LSTM (Long Short-Term Memory) networks. It explores the influence of musical context by incorporating MIDI data through an autoencoder, aiming to produce lyrics that not only make sense linguistically but also match the mood and style of the given music.

### Architecture Overview

The core architecture consists of two main components:
- **LSTM Model**: This model takes either plain text or concatenated text and MIDI embeddings as input to generate the next word in the sequence. It learns the patterns and sequences in the lyrics data, allowing it to produce coherent and creative text outputs.
- **MIDI Autoencoder**: This model is designed to compress MIDI data into a dense embedding, capturing the essential characteristics of the music. These embeddings can then be combined with word embeddings to provide a musical context for the lyrics generation process.

## Getting Started

### Prerequisites

Before running the project, ensure you have Python 3.x installed along with the following packages:
- torch
- gensim
- pretty_midi
- pandas


You can install all required packages using:
```bash
pip install -r requirements.txt
```

### Project Structure

```
project_root/
│
├── data/                # Raw and processed data files
├── jobs/                # Job scripts for HPC or cloud execution
├── legacy/              # Legacy code
├── models/              # Model definitions
│   ├── autoencoder.py   # MIDI autoencoder model
│   ├── lstm.py          # LSTM model for lyrics generation
│   └── weights/         # Saved model weights
├── notebooks/           # Jupyter notebooks for EDA and evaluation
├── scripts/             # Scripts for training models 
├── utils/               # Utility functions for data processing and training
├── lyrics_generator.py  # Main script for generating lyrics
├── requirements.txt     # Project dependencies
└── README.md            # This file
```

### How to Run the Model

#### 1. Preprocess the Data

Parse the lyrics and MIDI files to prepare them for training:

```bash
python utils/lyrics_parser.py
python utils/midi_parser.py
```

#### 2. Train the Model

Navigate to the `scripts` directory and run `train.py` with the desired configuration:

```bash
cd scripts/
python train.py --model lstm_midi --batch_size 64 --device cuda --learningrate 0.001 --epochs 10 --hidden_dim 128 --num_layers 2 --verbosity True --save True
```

Configuration options allow you to specify the model type, batch size, computation device, learning rate, number of epochs, hidden dimension size, number of recurrent layers, verbosity of the training process, and whether to save the model after training.

#### 3. Generate Lyrics

After training, you can generate lyrics using `lyrics_generator.py`:

```bash
python lyrics_generator.py
```

Once the lyrics generator is up and running, 
### Mock Examples of Generated Songs

Given a MIDI file for a "honesty billy joel", a song not in the training set, the model generated:

```
sometimes the wind blows outside 
following the stars we walk on 
when the line starts to waver
walk on by baby cause the moment is heaven
it hard work work 
i m in your days jeans out 
my mind are not had river size bows green 
you re not are never ever ever lie hands 
walk like i know what i m giving into 
baby crazy isn t forever give around running on by line 
walk on white new line heaven 
```

For the "hello world" MIDI, from the training set, the output was:

```
hello the world you my heart 
their name for all 
tell your heart 
million california dreaming tell you 
well hello it i call at you 
hello the other the other side 
hello from the other the other that 
oh anymore me made meet them 
tell me till me 
tell the other life 
but then make you 
hello that doesn t matter 
but i ve tried 
hello anymore on the outside difference 
hello from i m so burn anymore 
well before fell out it i re
```

These examples illustrate the versatility and creativity of the lyrics generation model, adapting its output to match the mood and style suggested by the MIDI context.

## Conclusion

This project demonstrates an innovative approach to lyrics generation, blending linguistic and musical information. The combination of LSTM models and MIDI autoencoders opens new possibilities for creative AI applications in music and beyond.
