# Deploy a Python Flask App on AWS Elastic Beanstalk

## Overview

This repository contains a sample Python Flask application that is deployed using AWS Elastic Beanstalk. This project demonstrates how to set up, deploy, and manage a Flask application in a scalable and managed environment on AWS.


- **`application/`**: Directory containing the Flask application code.
- **`requirements.txt`**: File listing the required Python packages.
- **`Procfile`**: Configuration file for Elastic Beanstalk to run the application.
- **`.ebextensions/01-python.config`**: Configuration file for Elastic Beanstalk environment settings.
- **`your-app.zip`**: Deployment package including all the necessary files.

## Prerequisites

- **AWS Account**: You need an AWS account to deploy the application.
- **AWS CLI**: Install and configure the AWS Command Line Interface.
- **Elastic Beanstalk CLI**: Optionally, install the Elastic Beanstalk CLI for easier management.

## Setup and Deployment

### 1. Prepare Your Flask Application

1. **Create the Flask App**:
   - Ensure the Flask app has the following structure:
     - `application/app.py`: Contains the main Flask application code.
     - `requirements.txt`: Lists all dependencies.
     - `Procfile`: Specifies how to run the Flask application.
     - `.ebextensions/01-python.config`: Configures Elastic Beanstalk settings.

2. **Configure Files**:
   - **`requirements.txt`**:
     ```plaintext
     Flask==2.0.1
     gunicorn==20.1.0
     ```
   - **`Procfile`**:
     ```plaintext
     web: gunicorn -b 0.0.0.0:8080 application.app:app
     ```
   - **`.ebextensions/01-python.config`**:
     ```yaml
     option_settings:
       aws:elasticbeanstalk:container:python:
         WSGIPath: application/app.py
     ```

### 2. Create Deployment Package

1. **Zip the Application**:
   - Create a zip file of your application files.
   - Command to create a zip file:
     ```bash
     zip -r your-app.zip *
     ```

### 3. Deploy on AWS Elastic Beanstalk

1. **Log in to AWS Management Console**:
   - Go to the [AWS Management Console](https://aws.amazon.com/console/).

2. **Open Elastic Beanstalk Console**:
   - Navigate to the Elastic Beanstalk service.

3. **Create a New Application**:
   - Click “Create Application,” enter a name for your application, and create it.

4. **Create a New Environment**:
   - Choose “Web server environment” and select “Python” as the platform.
   - Upload your zip file in the “Application Code” section.

5. **Configure Environment Settings**:
   - Review and configure instance traffic, scaling, and service access settings as needed.

6. **Review and Launch**:
   - Review all settings and click “Create environment” to deploy your application.

### 4. Monitor and Troubleshoot

1. **Check Environment Health**:
   - Use the Elastic Beanstalk console to monitor the health of your environment.

2. **View Logs**:
   - Access the logs from the “Logs” section in the Elastic Beanstalk console for troubleshooting.

3. **Restart Application**:
   - Restart your application from the Elastic Beanstalk console if needed.

## Additional Notes

- **Public IP Address**: By default, Elastic Beanstalk provides a URL for your application. Configure security groups and load balancer settings to control access.
- **Scaling and Resources**: Adjust auto-scaling and instance types based on your application's needs.

## License

This project is licensed under the [MIT License](LICENSE).

## Author

[Your Name] - [Your Contact Information]



