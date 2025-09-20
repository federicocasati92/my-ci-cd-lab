# CI/CD Lab: Flask App on AWS ECS Fargate

This project demonstrates how to build and deploy a Python (Flask) application on AWS ECS Fargate using an automated CI/CD workflow with GitHub Actions and Amazon ECR.

## 🔧 Technologies Used

- **Amazon ECS Fargate**: serverless container orchestration  
- **Amazon ECR**: private Docker image registry  
- **GitHub Actions**: CI/CD automation  
- **Flask**: Python web framework  
- **Docker**: containerization of the application  

## 📂 Project Structure

my-ci-cd-lab/
- `.github/`
  - `workflows/`
    - `ci-cd.yml`            # GitHub Actions workflow for CI/CD
- `ecs-task-json/`
  - `ecs-task-def.json`      # ECS Task Definition for Fargate
- `app.py`                   # Main Flask application
- `requirements.txt`         # Python dependencies
- `Dockerfile`               # Dockerfile to containerize the app
- `README.md`                # Project documentation

---

## 🚀 CI/CD Workflow

The project uses **GitHub Actions** to automate the following steps on every push to the `main` branch:

1. Build the Docker image.  
2. Push the image to Amazon ECR.  
3. Update the ECS task definition with the new image.  
4. Deploy the updated task to ECS Fargate.  

See `.github/workflows/ci-cd.yml` for the full workflow details.

---

## 🛠️ Prerequisites

- AWS account with permissions for ECR, ECS, and IAM  
- ECR repository created in AWS  
- ECS cluster and Fargate service configured  
- `ecs-task-def.json` correctly configured  

---

## 🔐 GitHub Secrets

Add the following secrets to your GitHub repository:

- `AWS_ACCESS_KEY_ID`: IAM access key  
- `AWS_SECRET_ACCESS_KEY`: IAM secret key  
- `AWS_REGION`: AWS region (e.g., `us-east-1`)  
- `ECR_REPOSITORY`: name of the ECR repository (e.g., `my-flask-app`)  

---

## 🌐 Accessing the Application

Once the task is running, access the Flask application in your browser using the task’s public IP and the configured port (e.g., `http://<public-ip>:5000`).

---

## 🧪 Testing the Application

```bash
#!/bin/bash

# Replace <task-arn> and <public-ip> with your actual values

# 1. Check the status of the ECS task
aws ecs describe-tasks --cluster flask-app --tasks <task-arn>

# 2. Send an HTTP request to the running Flask app
curl http://<public-ip>:5000
```
## 📄 Contributing

Contributions are welcome! Open issues or submit pull requests. Make sure to test changes locally before submitting.

---

## 📚 Useful References

* [AWS ECS Fargate Documentation](https://aws.amazon.com/ecs/)
* [GitHub Actions Deployment to AWS](https://docs.github.com/en/actions/deployment/targeting-aws-environments)
* [CI/CD with GitHub Actions and ECS Tutorial](https://dev.to/aws-builders/deploy-app-on-aws-ecs-fargate-using-github-actions-13mf)

```


