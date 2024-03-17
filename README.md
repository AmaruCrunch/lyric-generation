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

### Mock Examples of Generated Songs

Given a MIDI file for a soft ballad, the model might generate:

```
In the silence of the night
Whispers of a love so bright
Dreams that dance in moonlit skies
Tears that fall from your eyes
```

For an upbeat pop MIDI, the output could be:

```
Dance away, let the rhythm take you high
Under the glittering disco light
Feel the beat, as your heart comes alive
Tonight, we're gonna shine so bright
```

These examples illustrate the versatility and creativity of the lyrics generation model, adapting its output to match the mood and style suggested by the MIDI context.

## Conclusion

This project demonstrates an innovative approach to lyrics generation, blending linguistic and musical information. The combination of LSTM models and MIDI autoencoders opens new possibilities for creative AI applications in music and beyond.