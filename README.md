# Flask CI/CD Pipeline

A containerized Flask application with automated CI/CD deployment pipeline using GitHub Actions and AWS Elastic Beanstalk.

## Overview

This project demonstrates a complete DevOps workflow for a Flask web application, featuring automated testing, Docker containerization, and continuous deployment to AWS infrastructure.

## Features

- Simple Flask REST API with health check endpoint
- Docker containerization for consistent deployment
- Automated CI/CD pipeline with GitHub Actions
- AWS Elastic Beanstalk deployment
- Automated health checks and testing

## Project Structure

```
.
├── app.py                  # Flask application
├── Dockerfile             # Container configuration
├── requirements.txt       # Python dependencies
└── .github/
    └── workflows/
        └── deploy.yml     # CI/CD pipeline configuration
```

## Prerequisites

- Python 3.11+
- Docker
- AWS Account with Elastic Beanstalk configured
- GitHub repository

## Local Development

### Run with Python

```bash
pip install -r requirements.txt
python app.py
```

The application will be available at `http://localhost:5000`

### Run with Docker

```bash
docker build -t flask-cicd-app .
docker run -p 5000:5000 flask-cicd-app
```

## API Endpoints

- `GET /` - Returns welcome message
- `GET /health` - Health check endpoint returning JSON status

## CI/CD Pipeline

The GitHub Actions workflow automatically:

1. **Test Stage**

   - Checks out code
   - Sets up Python environment
   - Installs dependencies
   - Builds Docker image
   - Runs container and performs health checks

2. **Deploy Stage** (on main branch push)
   - Creates deployment package
   - Deploys to AWS Elastic Beanstalk

## AWS Configuration

Configure the following GitHub secrets for deployment:

- `AWS_ACCESS_KEY_ID` - AWS access key
- `AWS_SECRET_ACCESS_KEY` - AWS secret key
- `EB_APPLICATION_NAME` - Elastic Beanstalk application name
- `EB_ENVIRONMENT_NAME` - Elastic Beanstalk environment name
- `AWS_REGION` - AWS region (e.g., us-east-1)

## Dependencies

- Flask 3.0.0
- Werkzeug 3.0.1

## License

This project is available for educational and demonstration purposes.
