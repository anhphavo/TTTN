# Sugarcane Leaf Disease Detection System

This repository contains the source code and documentation for my graduation thesis:  
**"Research on Applying Transfer Learning and ResNet Technique to Build the Sugarcane Leaf Disease Detection System"**

##  Overview

The goal of this project is to build an AI-based system capable of detecting diseases in sugarcane leaves through image classification using deep learning. By applying **Transfer Learning** with the **ResNet50** architecture, the model can effectively identify multiple sugarcane leaf diseases from uploaded images.

This system is designed to support farmers, agricultural researchers, and developers in diagnosing plant health issues quickly and accurately.

##  Demo

![image](https://github.com/user-attachments/assets/7d8d4018-5b3f-4b49-a759-cb948d7e163b)
 
*A simple web interface where users can upload sugarcane leaf images and receive predictions.*

##  Key Features

- Image classification using a trained deep learning model.
- Fast and accurate predictions via a lightweight API.
- Simple web-based interface for end users.
- Dockerized deployment for consistent setup and scalability.
- Structured, maintainable, and modular project layout.

##  Project Structure

Diseases_Project_v2/
├── backend/
│ ├── model/ # Includes disease_model.keras and class_mapping.json
│ ├── main.py # FastAPI backend logic
│ └── utils.py # Helper functions for prediction
│
├── frontend/
│ ├── index.html # UI for image upload and prediction
│ ├── style.css # Basic styling
│ └── script.js # JavaScript logic to call API
│
├── docker-compose.yml # Container orchestration
├── requirements.txt # Python dependencies
├── README.md # Project documentation (this file)
└── .env # Environment variables (optional)


## ⚙️ Tech Stack

| Component    | Technology         |
|--------------|--------------------|
| Model        | TensorFlow / Keras |
| Architecture| ResNet50 (Transfer Learning) |
| Backend API  | FastAPI (Python)   |
| Frontend     | HTML, CSS, JavaScript |
| Database     | PostgreSQL (optional) |
| Deployment   | Docker, Docker Compose |

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Docker & Docker Compose installed
- Git installed

### Clone the Repository

```bash
git clone https://github.com/your-username/sugarcane-disease-detector.git
cd Diseases_Project_v2

### Run with Docker
[docker-compose up --build]
Once the containers are up, access the app at:
[http://localhost:8000]
📊 Model Details
Model Used: ResNet50 (fine-tuned)

Input Image Size: 128x128 pixels

Output: Disease class + prediction confidence

File: disease_model.keras

Class Labels: Defined in class_mapping.json

Dataset
Source: Mendeley Data - Sugarcane Leaf Disease Dataset

Classes: Healthy, Red Rot, Rust, Mosaic

Preprocessing: Resized, normalized, augmented

🧪 Sample Prediction Flow
User uploads an image via the frontend.

Image is sent to the FastAPI backend.

Backend loads the trained model and returns the predicted class + confidence.

Result is displayed on the UI.

✅ TODO / Future Improvements
 Train MobileNet and compare accuracy vs ResNet50

 Support image upload via mobile

 Add language toggle (English/Vietnamese)

 Build admin dashboard for history tracking

 Enable database logging for predictions

