# Student Exam Performance Indicator

Welcome to the **Student Exam Performance Indicator** [web application](http://ec2-3-238-242-162.compute-1.amazonaws.com:8080/)! This system is designed to analyze and predict students' academic performance based on various input factors, primarily focusing on predicting a student's math score.

## Project Overview

The Student Exam Performance Indicator utilizes machine learning techniques to predict students' math scores based on their personal and academic data. The system takes into account factors such as gender, parental education level, test preparation status, and scores in reading and writing.

The project is deployed on an AWS EC2 instance, with containerized management using AWS Elastic Container Registry (ECR). The model was trained using the **Students Performance in Exams** dataset from Kaggle.

## Dataset Details

The dataset used in this project contains the following features for prediction:

- **Gender**: Indicates the gender of the student (e.g., male or female).
- **Race/Ethnicity**: Categorizes students based on race/ethnicity (e.g., group A, group B, etc.).
- **Parental Level of Education**: Represents the highest level of education completed by the student's parent or guardian.
- **Lunch**: Indicates the type of lunch the student receives (e.g., standard or free/reduced).
- **Test Preparation Course**: Specifies whether the student completed a test preparation course (completed or none).
- **Reading Score**: The score obtained by the student in the reading test.
- **Writing Score**: The score obtained by the student in the writing test.

## Key Features

Our web application provides:

- An intuitive interface for entering student details.
- Real-time predictions of math scores based on input data.
- A user-friendly and effective experience for predicting student performance.

## Deployment Details

This project is deployed on an AWS EC2 instance. The deployment leverages AWS Elastic Container Registry (ECR) for containerized management of the application.

### How It Works:
- The machine learning model was trained using the above features, and predictions are made based on student input on the prediction page.
- The app provides a prediction of the student's math score once all required details are entered.

## Try It Out

- **Home**: Visit the home page to get an overview of the project.
- **Prediction Page**: Head to the prediction page to enter student details and get predictions for the math score.
- **About**: Learn more about the project and how it works.

## Explore the Source Code

You can find the source code and contribute to the project on our [GitHub repository](https://github.com/your-username/student-exam-performance-indicator).

## How to Set Up Locally

### Prerequisites:
- Python 3.x
- Flask
- Docker (for containerized deployment)
- AWS CLI (for managing EC2 instances and ECR)

### Installation:
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/student-exam-performance-indicator.git
   cd student-exam-performance-indicator

2. Set up a virtual environment and install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows, use venv\Scripts\activate
   pip install -r requirements.txt
3. Set Up Amazon ECR (Elastic Container Registry)

   To store your Docker images, you need to set up an ECR repository.
   
   Create an ECR Repository:
   1. Open the [Amazon ECR Console](https://console.aws.amazon.com/ecr/).
   2. Click on **Repositories** in the sidebar.
   3. Click **Create repository**.
   4. Choose a name for your repository (e.g., `simple-app`).
   5. Select the appropriate settings (public or private).
   6. Click **Create repository**.



4. Set Up IAM User for AWS Access

   To interact with AWS services such as ECR, you need to set up an IAM user with the necessary permissions.
   
   Create an IAM User:
   1. Open the [IAM Console](https://console.aws.amazon.com/iam/).
   2. Click on **Users** in the sidebar.
   3. Click **Add user**.
   4. Provide a username (e.g., `docker-user`).
   5. Select **Programmatic access** (this gives access via the AWS CLI and API).
   6. Click **Next: Permissions**.
   
   Assign Permissions:
   1. Choose **Attach policies directly**.
   2. Search for and select the following policies:
      - `AmazonEC2ContainerRegistryFullAccess`
      - `AmazonS3ReadOnlyAccess` (optional, if you need S3 access)
   3. Click **Next: Tags**, then **Next: Review**, and finally **Create user**.
   
   #### Save Access Keys:
   1. After creating the IAM user, you will see an **Access key ID** and **Secret access key**.
   2. Save these credentials securely, as you will use them to configure your AWS CLI and authenticate with ECR.


5. To set up Docker in your AWS EC2 instance:
   Before installing Docker, it's a good idea to update your system packages.
   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade -y
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
6. Configure EC2 as a Self-Hosted Runner for GitHub Actions:
   To set up the EC2 instance as a self-hosted runner for GitHub Actions, follow these steps:
   
   Setup GitHub Secrets:
   
   You need to configure AWS credentials and the ECR login URI as GitHub secrets to interact with AWS services. These secrets should be set in your GitHub repository under Settings > Secrets and Variables > Actions.
   
   AWS_ACCESS_KEY_ID: Your AWS Access Key ID.
   AWS_SECRET_ACCESS_KEY: Your AWS Secret Access Key.
   AWS_REGION: Set this to your AWS region (e.g., us-east-1).
   AWS_ECR_LOGIN_URI: This is the URI for your Amazon Elastic Container Registry (ECR).


7. Run the Flask app in EC2:
    ```bash

   ./run.sh

8. After running the app, visit the website using the public IPv4 address shared by your EC2 instance in your browser to interact with the application.
