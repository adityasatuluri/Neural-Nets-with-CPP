# Neural Networks from Scratch in C++

This project contains implementations of three types of neural networks built from scratch in C++ using only the standard library (no external dependencies like TensorFlow or OpenCV). The networks include a Convolutional Neural Network (CNN), a Recurrent Neural Network (RNN), and a Multi-Layer Perceptron (MLP), each designed to demonstrate fundamental concepts of neural network architectures with step-by-step logging and time delays for educational purposes.

## Table of Contents
- [Overview](#overview)
- [Requirements](#requirements)
- [Setup](#setup)
- [Usage](#usage)
  - [Convolutional Neural Network (CNN)](#convolutional-neural-network-cnn)
  - [Recurrent Neural Network (RNN)](#recurrent-neural-network-rnn)
  - [Multi-Layer Perceptron (MLP)](#multi-layer-perceptron-mlp)
- [Limitations](#limitations)
- [Future Improvements](#future-improvements)
- [License](#license)

## Overview
This repository showcases:
- **CNN**: Processes 8x8 binary "images" (e.g., X and O patterns) for binary classification using convolution, max pooling, and a fully connected layer.
- **RNN**: Predicts the next value in a sequence (e.g., `[0.1, 0.2, 0.3]` -> `0.4`) using recurrent connections and Backpropagation Through Time (BPTT).
- **MLP**: Solves the XOR problem with a simple feedforward network, demonstrating basic backpropagation.

Each implementation includes detailed logging of the forward and backward passes, with `std::this_thread::sleep_for` delays to visualize the computation steps.

## Requirements
- A C++ compiler supporting C++11 or later (e.g., `g++`, `clang++`, or MSVC).
- Standard C++ libraries: `<iostream>`, `<vector>`, `<cmath>`, `<cstdlib>`, `<ctime>`, `<chrono>`, `<thread>`.

No external libraries are required.

## Setup
1. **Clone or Download**: Obtain the source files (`cnn.cpp`, `rnn.cpp`, `mlp.cpp`).
2. **Compile**:
   - For CNN: `g++ -std=c++11 cnn.cpp -o cnn`
   - For RNN: `g++ -std=c++11 rnn.cpp -o rnn`
   - For MLP: `g++ -std=c++11 mlp.cpp -o mlp`
3. **Run**:
   - `./cnn` (or `cnn.exe` on Windows)
   - `./rnn`
   - `./mlp`

## Usage

### Convolutional Neural Network (CNN)
- **File**: `cnn.cpp`
- **Purpose**: Classifies 8x8 binary images into two categories (e.g., "X" shape = 1, "O" shape = 0).
- **Structure**:
  - Input: 8x8 grid
  - Convolutional Layer: 3x3 filter -> 6x6 feature map
  - Max Pooling: 2x2 window -> 3x3 pooled output
  - Fully Connected Layer: 4 hidden neurons -> 1 output
- **Execution**:
  - Trains on two hardcoded 8x8 patterns for 10 epochs.
  - Tests on training data and a separate test image.
- **Output**: Displays image patterns, training progress, and predictions.
- **Modification**: Replace `test_image` in `main()` with your own 8x8 matrix (0.0 or 1.0 values).

### Recurrent Neural Network (RNN)
- **File**: `rnn.cpp`
- **Purpose**: Predicts the next value in a sequence (e.g., `[0.1, 0.2, 0.3]` -> `0.4`).
- **Structure**:
  - Input: 1 scalar per timestep
  - Hidden Layer: 4 neurons with recurrent connections
  - Output: 1 scalar
- **Execution**:
  - Trains on a 3-step sequence for 10 epochs.
  - Tests prediction on the same sequence.
- **Output**: Logs forward and backward passes per timestep, with final prediction.
- **Modification**: Adjust `sequence` and `targets` in `main()` to train on different sequences.

### Multi-Layer Perceptron (MLP)
- **File**: `mlp.cpp`
- **Purpose**: Solves the XOR problem (e.g., `[0,0]` -> `0`, `[0,1]` -> `1`).
- **Structure**:
  - Input: 2 neurons
  - Hidden Layer: 4 neurons
  - Output: 1 neuron
- **Execution**:
  - Trains on 4 XOR input-target pairs for 5 epochs.
  - Tests on the training data.
- **Output**: Shows training steps and predictions with binary classification (0 or 1).
- **Modification**: Change `inputs` and `targets` in `main()` for other binary classification tasks.

## Limitations
- **CNN**:
  - Limited to 8x8 binary inputs; no real image file loading (requires external libraries).
  - Single filter; real CNNs use multiple filters.
- **RNN**:
  - Fixed sequence length (3 timesteps); no dynamic resizing.
  - Predicts only the final output, not per timestep.
- **MLP**:
  - Small-scale problem (XOR); not tested on larger datasets.
- **General**:
  - Sleep delays slow execution, intended for demonstration.
  - No error handling for invalid inputs or sizes.

## Future Improvements
- Add support for loading real images (e.g., via a library like libpng).
- Implement multiple filters in the CNN.
- Extend the RNN to handle variable-length sequences and multi-output predictions.
- Optimize by removing sleeps and adding batch processing.
- Include command-line arguments for custom inputs and parameters.

## License
This project is unlicensed and free to use for educational purposes. Feel free to modify and distribute as needed.