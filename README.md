# Football Object Detection Using Custom YOLO11n

A computer vision project that uses a custom-trained YOLO11n model to detect football players, goalkeepers, referees, and the ball in football images and videos.

## Project Overview

The goal of this project is to explore how computer vision can automate object detection in football footage. The model was trained using a football detection dataset from Roboflow and evaluated on unseen test images.

### Current Capabilities

- Detect players, goalkeepers, referees, and the ball.
- Run inference on football images and videos.
- Export the trained model to ONNX for compatible inference environments.

### Detection Classes

| Class | Description |
|---|---|
| `ball` | Football |
| `goalkeeper` | Goalkeeper |
| `player` | Outfield player |
| `referee` | Match official |

## Model and Dataset

- **Model:** YOLO11n
- **Image size:** 640 × 640
- **Training environment:** Google Colab with an NVIDIA T4 GPU
- **Dataset:** [Football Players Detection — Roboflow Universe](https://universe.roboflow.com/roboflow-jvuqo/football-players-detection-3zvbc)
- **Dataset version:** 15
- **Dataset license listed by Roboflow:** CC BY 4.0

The dataset contains 372 images: 298 for training, 49 for validation, and 25 for testing.

## Test Results

Evaluation on the 25-image test set:

| Metric | Result |
|---|---:|
| Precision | 87.0% |
| Recall | 78.9% |
| mAP@50 | 79.7% |
| mAP@50–95 | 50.5% |

### Per-Class mAP@50

| Class | mAP@50 |
|---|---:|
| Ball | 26.8% |
| Goalkeeper | 97.8% |
| Player | 98.2% |
| Referee | 96.0% |

The model performs well on player, goalkeeper, and referee detection. Ball detection remains a major limitation, with a test recall of approximately 29.1%.

The test set is small, so these results should be considered preliminary rather than a guarantee of real-world performance.

## Repository Structure

```text
football-object-detection-yolo11n/
├── models/
│   ├── best.pt
│   └── best.onnx
├── notebooks/
│   └── football_yolo11n_training.ipynb
├── requirements.txt
└── README.md
```

## Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/jihedsaguer/football-object-detection-yolo11n.git
cd football-object-detection-yolo11n
```

### 2. Install dependencies

Create and activate a virtual environment, then install the required packages:

```bash
pip install -r requirements.txt
```

### 3. Run inference

The following Python example loads the trained PyTorch model and predicts objects in an image:

```python
from ultralytics import YOLO

model = YOLO("models/best.pt")

results = model.predict(
    source="path/to/football_image.jpg",
    imgsz=640,
    conf=0.25,
    save=True
)
```

Replace `path/to/football_image.jpg` with the path to your own image.

## Future Improvements

- Improve ball detection using more representative training data.
- Evaluate the model on a larger and more diverse test set.
- Add multi-object tracking across video frames.
- Explore team classification and player movement analysis.
- Develop a user-friendly interface for football video analysis.

## Limitations and Responsible Use

This project currently focuses on object detection. It does not yet identify individual players, reliably calculate possession, or generate complete tactical analysis.

Use football footage only when you have the appropriate rights or permission. The dataset's stated license does not automatically grant rights to every underlying image or match recording.

## Acknowledgements

Dataset: [Football Players Detection — Roboflow Universe](https://universe.roboflow.com/roboflow-jvuqo/football-players-detection-3zvbc).

This project was developed for educational and portfolio purposes.
