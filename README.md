# Scene Text Recognition (STR)

This **Scene Text Recognition** project focuses on **detecting** and **recognizing** text in images, commonly known as **OCR** (**Optical Character Recognition**). The project leverages **YOLO** for text detection and a **CRNN model** (CNN + RNN + CTC Loss) for text recognition.

This document provides a detailed explanation of the pipeline, including data preparation, model training, evaluation, and deployment using **Ray** + **FastAPI**.


## 1. Main Objectives & Pipeline

![alt text](image-1.png)

- **Text Detection**: Identifies bounding boxes of words (or phrases) within an image.
- **Text Recognition**: Decodes text content from each bounding box.
- **Inference Deployment**: Provides an API endpoint (via FastAPI + Ray) and a Streamlit interface to allow users to upload images or specify image URLs for OCR.

## 2. Project Structure and Main Files

Below is the folder structure, along with an overview of each file’s role:
```bash
Scene-Text-Recognition
├── STR-phase-1-detection.ipynb    # Train text detection model
├── STR-phase-2-recognition.ipynb  # Train text recognition model
├── STR-phase-3-inference.ipynb    # Full pipeline inference (detection + recognition)
├── deployment
│   ├── object_detection.py        # YOLO-based text detection API (FastAPI)
│   ├── crnn.py                    # CRNN model
│   ├── ocr.py                     # Full OCR service (Detection + Recognition)
│   ├── app.py                     # Streamlit-based UI
│   ├── Makefile                   # Deployment scripts
│   └── __init__.py
└── weights
    ├── best.pt                    # Trained YOLO weights
    └── ocr_crnn.pt                # Trained CRNN weights
```

## 3. Installation

To run this project, you will need:

- Python 3.10
- CUDA (if using GPU)
- Required libraries from `requirements.txt`

```bash
# Set up a virtual environment
python -m venv env
source env/bin/activate

# Install PyTorch (Optional: GPU Support)
# https://pytorch.org/get-started/previous-versions/
conda install pytorch==2.5.1 torchvision==0.20.1 torchaudio==2.5.1 pytorch-cuda=12.4 -c pytorch -c nvidia

# Install dependencies
pip install -r requirements.txt
```

## 4. Usage

**Note**: Make sure your device has the **make** command installed. If not, you can use Git Bash or get it from [here](https://www.mingw-w64.org/).

```bash
# Initialize the environment
cd deployment
make init

# Start OCR service (Ray + FastAPI)
make deploy_ocr

# Launch Streamlit app for UI-based inference
make streamlit
```

## 5. Others

- This project is assigned by AIO course from AI VIET NAM and completed by student.
- This project is licensed under the [Apache License](LICENSE).
- For any questions or feedback, please open an issue or contact:
    - Study Email: lehuuphuoc2502yuitc@gmail.com
    - Main Email: tainguyenphu2502@gmail.com