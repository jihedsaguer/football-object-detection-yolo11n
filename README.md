Football Object Detection Using Custom YOLO11n
A computer vision project that uses a custom-trained YOLO11n model to detect football players, goalkeepers, referees, and the ball in football images and videos.
Project Overview
The goal of this project is to explore how computer vision can automate object detection in football footage. The model was trained using a football dataset from Roboflow and evaluated on unseen test images.
Current capabilities
* Detect players, goalkeepers, referees, and the ball.
* Run inference on football images and videos.
* Export the trained model to ONNX for compatible inference environments.
Classes
ClassDescriptionballFootballgoalkeeperGoalkeeperplayerOutfield playerrefereeMatch officialModel and Dataset
* Model: YOLO11n
* Image size: 640 × 640
* Training: Google Colab with NVIDIA T4 GPU
* Dataset: Football Players Detection — Roboflow Universe
* Dataset version: 15
* Dataset license listed by Roboflow: CC BY 4.0
The dataset contains 372 images: 298 training images, 49 validation images, and 25 test images.
Test Results
Evaluation on the 25-image test set:
MetricResultPrecision87.0%Recall78.9%mAP@5079.7%mAP@50–9550.5%Per-Class mAP@50
ClassmAP@50Ball26.8%Goalkeeper97.8%Player98.2%Referee96.0%The model performs well on player, goalkeeper, and referee detection. Ball detection remains a major limitation, with a test recall of approximately 29.1%. The test set is small, so these results should be treated as preliminary rather than as a guarantee of real-world performance.
Repository Structure
football-object-detection-yolo11n/
??? models/
?   ??? best.pt
?   ??? best.onnx
??? notebooks/
?   ??? football_yolo11n_training.ipynb
??? requirements.txt
??? README.md
Getting Started
1. Clone the repository
git clone YOUR_GITHUB_REPOSITORY_URL
cd football-object-detection-yolo11n
2. Install dependencies
Create and activate a virtual environment, then run:
pip install -r requirements.txt
3. Run inference
The following Python example loads the trained PyTorch model and predicts objects in an image:
from ultralytics import YOLO

model = YOLO("models/best.pt")

results = model.predict(
    source="path/to/football_image.jpg",
    imgsz=640,
    conf=0.25,
    save=True
)
Replace path/to/football_image.jpg with the path to your own image.
Future Improvements
* Improve ball detection using more representative training data.
* Evaluate on a larger and more diverse test set.
* Add multi-object tracking across video frames.
* Explore team classification and player movement analysis.
* Develop a user-friendly interface for football video analysis.
Limitations and Responsible Use
This project currently focuses on object detection; it does not yet identify individual players, reliably calculate possession, or generate complete tactical analysis.
Use football footage only when you have the appropriate rights or permission. The dataset's stated license does not automatically grant rights to every underlying image or match recording.
Acknowledgements
Dataset: Football Players Detection — Roboflow Universe.
This project was developed for educational and portfolio purposes.

