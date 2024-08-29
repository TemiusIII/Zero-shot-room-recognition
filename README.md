# Zero-Shot Room Recognition with LLaVA-NeXT

This repository contains the implementation of a zero-shot room recognition system using LLaVA-NeXT and Qwen. The project processes a dataset of interior room images to identify objects within the room and classify the room type.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Dataset](#dataset)
- [Model Details](#model-details)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Introduction

This project implements a zero-shot room recognition system that utilizes the LLaVA-NeXT model to extract and describe objects in a room from a sequence of images. The identified objects are then passed through the Qwen text-based neural network to classify the room into predefined room types based on object presence probabilities.

## Features

- **Object Detection:** Uses LLaVA-NeXT to detect and describe objects in the room.
- **Room Type Classification:** Employs Qwen to classify the room type based on detected objects.
- **Zero-Shot Learning:** Capable of recognizing rooms without requiring training on the specific dataset.
- **Efficient Data Processing:** Utilizes Python sets to ensure unique object detection before classification.

## Installation

To get started, clone the repository and install the necessary dependencies:

```bash
# install LLaVA-NeXT 
git clone https://github.com/LLaVA-VL/LLaVA-NeXT llava
cd llava
conda create -n llava python=3.10 -y
conda activate llava
pip install --upgrade pip
pip install -e ".[train]"

# to make notebook work properly
pip install ipykernel
python -m ipykernel install --user --name llava --display-name "Python(llava)"
```

Also don't forget about dataset
```bash
 python donwnload_data.py --preprocessed_frames -o data
  ```

## Usage

1. **Run the notebook :)**

   ```bash
   conda activate llava 
   jupyter notebook
   ```
2. **Paste your hf token**:
 
    Unfortunately meta-llama/Meta-Llama-3-8B-Instruct is gated, so you need apply for access
 
3. **View Results:**

   The classification results will be displayed in the last cell.

## Dataset

The `scannet_frames_25k` dataset is used as the input for this project. It contains sequences of interior room images captured from various angles, ideal for object detection and room classification tasks.

- [ScanNet Dataset](http://www.scan-net.org/)

## Model Details

### LLaVA-NeXT

[llama-llava](https://huggingface.co/lmms-lab/llama3-llava-next-8b) is utilized for object detection and description. It processes the input images and identifies objects present in the room.

### Qwen

[Qwen](https://huggingface.co/Qwen/Qwen2-7B-Instruct) is a text-based neural network that takes the list of detected objects and predicts the probability of the room belonging to specific room types.

## Results

The project has been tested on various room types, and it effectively classifies rooms into categories such as:

- Living Room
- Bedroom
- Kitchen
- Bathroom
- Office

The results are based on zero-shot learning, meaning the model has not been trained on the `scannet_frames_25k` dataset but still accurately classifies room types based on object detection.

## Contributing

Contributions are welcome! If you'd like to contribute to this project, please fork the repository and submit a pull request. For major changes, please open an issue to discuss what you would like to change.


## License

This project is licensed under the Apache 2.0 License. See the [LICENSE](https://github.com/TemiusIII/Zero-shot-room-recognition/blob/main/LICENSE) file for more details.
