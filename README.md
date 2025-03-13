# Automated-CI-CD-with-Jenkins
A small learning project where i try to automate CI/CD with jenkins

I have set up a Jenkins server that is configured to run continuous integration / continuous deployument pipelines automatically.

Git Integration: Jenkins is connected to my GitHub repository and it's configured to listen for changes in the main branch of my repository.
Pipeline: My Jenkins pipeline performs several key tasks whenever changes are made to the repository:

    Clone Repository: Jenkins pulls the latest code from my GitHub repository whenever a change is detected.
    Build Docker Image: Jenkins builds a Docker image for my Python application (my-python-app) using the Dockerfile in my repo.
    Run Tests: Jenkins runs my tests (using pytest in this case) to ensure that everything works as expected.
    Push to DockerHub: After the tests pass, Jenkins pushes the built Docker image to Docker Hub under my swelo account, making it available for anyone to pull and use.
    Deploy: Finally, Jenkins deploys the Docker container to my server (or local machine) and runs it on port 5000.

Docker Hub: The image i've built and pushed to Docker Hub is now available for deployment or sharing. This means that anyone with Docker can pull it and run the app locally or on a cloud server.
