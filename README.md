<<<<<<< HEAD
# Autism Disorder Detection System Using Deep Learning
=======
# Autism Disorder Detection System
>>>>>>> 958a232ffec1b980331256adbcc91d4b7067aea5

A Flask-based web application that uses deep learning and computer vision techniques for experimental Autism Spectrum Disorder (ASD) image classification. The system captures multiple facial images, verifies facial identity across captures, and generates individual and aggregated predictions using a trained MobileNetV2 model.

## Features

- **User Authentication:** User registration and login with securely hashed passwords.
- **Photo Plan:** Configure an image capture plan from 1 to 10 photos.
- **Face Detection:** Uses MTCNN to detect faces in captured images.
- **Face Verification:** Uses FaceNet to generate facial embeddings and cosine similarity to verify that the same person is captured throughout the session.
- **ASD Image Classification:** Uses a trained MobileNetV2 model to generate a prediction probability from facial images.
- **Capture Interval:** Enforces a 3-second delay between image captures.
- **Result Aggregation:** Calculates the mean prediction probability across the captured images to generate a final result.
- **User Dashboard:** Displays previous captures, individual predictions, and the final aggregated result.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Backend | Flask |
| Frontend | HTML, CSS, JavaScript |
| Deep Learning | TensorFlow, Keras, MobileNetV2 |
| Face Detection | MTCNN |
| Face Recognition | FaceNet |
| Image Processing | OpenCV, NumPy |
| Similarity Measurement | Scikit-learn, Cosine Similarity |
| Database | SQLite |
| ORM | Flask-SQLAlchemy |

## Project Structure

```text
autism-disorder-detection-system/
│
├── app.py
├── autism_mobilenetv2.h5
├── requirements.txt
├── .gitignore
│
├── static/
│   ├── css/
│   │   └── style.css
│   └── js/
│       └── main.js
│
├── templates/
│   └── index.html
│
├── users/                 # Captured user images
│
└── instance/              # SQLite database
```

## How It Works

1. **User Login:** Users register or log in to access the application.
2. **Photo Plan Creation:** Users select the number of images to capture, from 1 to 10.
3. **Face Detection:** MTCNN detects and extracts the face from each captured image.
4. **Face Verification:** FaceNet generates facial embeddings. Cosine similarity is used to check whether the captured face matches the first image.
5. **Image Classification:** The detected face is processed and passed to the trained MobileNetV2 model.
6. **Prediction Aggregation:** The application calculates the mean prediction probability across all captures.
7. **Final Result:** The aggregated probability is used to display the final classification.

### Prediction Logic

The application uses a probability threshold of 0.50:

- Probability greater than 0.50 → Autistic
- Probability less than or equal to 0.50 → Non-Autistic

This class mapping assumes that the model was trained with the Autistic class encoded as the positive class (1).

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/autism-disorder-detection-system.git
```

```bash
cd autism-disorder-detection-system
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

Activate it on Windows:

```bash
venv\Scripts\activate
```

On Linux/macOS:

```bash
source venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
```

Install the required application packages:

```bash
pip install Flask Flask-SQLAlchemy Flask-CORS Werkzeug python-dotenv
pip install tensorflow opencv-python numpy
pip install mtcnn keras-facenet scikit-learn
```

**Note:** TensorFlow, OpenCV, NumPy, and MTCNN versions must be compatible with your Python environment. The commands above install packages but do not guarantee compatibility with every operating system.

### 4. Configure Environment Variables

Create a `.env` file in the project root:

```env
FLASK_SECRET_KEY=replace_with_a_secure_random_secret
DATABASE_URL=sqlite:///users.sqlite3
```

Keep `.env` private and do not upload it to GitHub.

### 5. Run the Application

```bash
python app.py
```

Open the application in your browser:

```text
http://127.0.0.1:5000
```

## Model Information

The project uses the trained model:

`autism_mobilenetv2.h5`

- **Architecture:** MobileNetV2
- **Input Image Size:** 224 × 224 pixels
- **Output:** Binary classification probability
- **Classification Threshold:** 0.50

The model file must be present in the project root directory for predictions to work.

## Configuration

The following settings are defined in `app.py`:

| Parameter | Default Value | Purpose |
|---|---:|---|
| `FACE_MATCH_THRESHOLD` | 0.55 | Face similarity threshold |
| `ASD_THRESHOLD` | 0.50 | Classification threshold |
| `CAPTURE_DELAY` | 3 seconds | Delay between image captures |
| `IMG_W` | 224 | Model input width |
| `IMG_H` | 224 | Model input height |

## Future Improvements

- Improve model evaluation using independent test datasets.
- Add more detailed prediction history and reporting.
- Improve the user dashboard and visualization.
- Add additional model performance metrics.
- Improve application deployment and security.

## Disclaimer

This project is developed for academic and educational purposes. Its image-based predictions are experimental and are not a clinically validated method for diagnosing Autism Spectrum Disorder. The results should not be used as a substitute for professional medical assessment.

## Author

**Shreya V K**

- GitHub: [Shreyavk28](https://github.com/Shreyavk28)
- LinkedIn: [Shreya VK](https://linkedin.com/in/shreya-vk-softwareengineer)