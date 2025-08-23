**Automated CI/CD Pipeline for Web Application Deployment**
This sample project demonstrates a complete, end-to-end CI/CD pipeline that automates the process of building, testing, and deploying a containerized web application. The pipeline integrates Git for version control, Jenkins for automation, SonarQube for code quality analysis, and Docker for containerization and deployment.

**Architecture:**
The pipeline follows a modern DevOps workflow, where every code push to the main branch on GitHub automatically triggers a series of automated steps to ensure the code is high-quality and deployed seamlessly.

**Workflow Diagram**
+-----------------+      +-----------------+      +-----------------+      +-----------------+      +-----------------+
|                 |      |                 |      |                 |      |                 |      |                 |
|   GitHub        +------>  Jenkins        +------>  SonarQube      +------>  Docker Build   +------>  Deploy to Server|
| (Code Commit)   |      | (CI/CD Server)  |      | (Code Analysis) |      | (Containerize)  |      | (Production)    |
|                 |      |                 |      |                 |      |                 |      |                 |
+-----------------+      +-----------------+      +-----------------+      +-----------------+      +-----------------+



**Technologies Used:**
- Version Control: Git & GitHub
- CI/CD Automation: Jenkins
- Code Quality: SonarQube
- Containerization: Docker
- Deployment Target: AWS EC2 Instance (Ubuntu) with Docker installed

**Pipeline Stages:**
The Jenkins pipeline is defined using a Jenkinsfile and is broken down into the following key stages:

1. Checkout
Action: The pipeline checks out the latest code from the main branch of the GitHub repository.

Trigger: This stage is automatically triggered by a webhook upon a git push event.

2. Code Analysis with SonarQube
Action: The source code is analyzed by SonarQube to detect bugs, vulnerabilities, and code smells.

Purpose: This ensures that the code adheres to quality standards before it proceeds to the deployment phase. The pipeline can be configured to fail if the code does not pass the defined quality gates.

3. Build Docker Image
Action: Jenkins uses a Dockerfile located in the repository to build a Docker image of the web application.

Purpose: This containerizes the application, packaging it with all its dependencies into a portable and consistent runtime environment.

4. Deploy to Production
Action: The pipeline connects to a remote Linux server via SSH. It stops and removes any old version of the container and then runs the newly built Docker image.

Result: The latest version of the web application is now live and accessible to users.

**How It Works:**
- A developer pushes code changes to the GitHub repository.
- A GitHub webhook notifies the Jenkins server of the new commit.
- Jenkins automatically starts the pipeline, checking out the code.
- The SonarQube scanner is invoked to perform static code analysis.
- If the code quality check passes, Jenkins proceeds to build a new Docker image.
- Finally, Jenkins securely connects to the production server, stops the old container, and starts the new one, completing the deployment.

**Notes:**
- This is a learning project, not production-ready code.
- Demonstrates understanding of CI/CD workflow, DevOps tools, and cloud deployment.
- All AWS resources were terminated after the learning phase to avoid charges.
