# Tailor Vision

Tailor Vision is a small computer vision application built with Python and Streamlit. It provides two tools:

- Virtual Try-On for previewing accessories and clothing on a captured photo.
- Body Measurement for estimating shoulder, chest, and waist measurements from a full-body photo.

The project is intended to run locally. It does not require Docker or any separate deployment setup.

## Features

### Virtual Try-On

The Virtual Try-On module uses face landmarks to place selected items on a photo. The available assets include:

- Hats
- Goggles
- Dresses
- Necklaces
- Earrings
- Tiaras
- Flowers

A photo can be captured directly from the browser. The processed result can then be saved as a PNG file.

### Body Measurement

The Body Measurement module uses pose estimation to produce estimated:

- Shoulder measurement
- Chest measurement
- Waist measurement
- Clothing size

The result can also be exported as a PDF report.

## Tech Stack

- Python
- Streamlit
- OpenCV
- MediaPipe
- dlib
- NumPy
- Pillow
- imutils
- fpdf2

## Project Structure

```text
tailor-vision/
├── app/
│   ├── Home.py
│   └── pages/
│       ├── 1_Virtual_Try_On.py
│       └── 2_Body_Measurement.py
│
├── tailor_vision/
│   ├── catalog.py
│   ├── config.py
│   ├── imaging.py
│   ├── exceptions.py
│   ├── tryon/
│   └── measurement/
│
├── assets/
│   ├── images/
│   └── models/
│
├── scripts/
│   └── download_model.py
│
└── requirements.txt
```

## Requirements

Python 3.10, 3.11, or 3.12 is recommended.

The project depends on packages that may not yet support newer Python versions, so avoid using Python 3.13 or newer.

## Installation

Clone the repository and open a terminal in the project directory.

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```bash
.venv\Scripts\activate
```

On macOS or Linux:

```bash
source .venv/bin/activate
```

Install the required packages:

```bash
pip install -r requirements.txt
```

## Face Landmark Model

The Virtual Try-On feature requires the dlib face landmark model.

From the project root, run:

```bash
python scripts/download_model.py
```

This downloads the required model into:

```text
assets/models/
```

If the model is already present there, this step is not required again.

## Running the Application

Start Streamlit with:

```bash
streamlit run app/Home.py
```

Streamlit will open the application in your browser.

The sidebar can then be used to switch between Virtual Try-On and Body Measurement.

## Notes

The measurements produced by this project are estimates based on computer vision and should not be treated as professional tailoring measurements.

For better results, use clear, well-lit photos. For body measurement, the full body should be visible and the person should be facing the camera.

The application is designed primarily for local use and keeps the processing on the machine running the application.

## License

This project is available for personal and educational use.
