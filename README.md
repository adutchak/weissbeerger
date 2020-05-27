## How to start Jenkins & WEB app:
1. Using docker-compose, start Jenkins:

   ``
         docker-compose up -d weissbeerger-jenkins 
   ``

   This will also pull a pre-built public image: **adutchak/weissbeerger-jenkins-with-docker:2.238-alpine** with Jenkins & docker pre-installed.

   Dockerfile for Jenkins is located in the folder: **docker-images/weissbeerger-jenkins-with-docker**.
   It inherits official Jenkins image + makes docker installation (to be able to build docker images from the docker container).

   Folder **./jenkins-home** (used in Dockerfile) has been excluded from the repository since it's massive and contains only Jenkins-specific (no jobs) settings.

   **./jenkins-jobs** folder contains Job's configuration data as requested in the task.

2. To build **weissbeerger-web** application as requested in the exercise (assuming we'll be relying on local docker images cache, without push\pull proccess involved) - use pipeline named **"Weissbeerger web app"**. 

   Each time you're triggering the job, the image will be built & tagged with current build number (i.e. weissbeerger-web:v1, weissbeerger-web:v2 etc.).

   This version is referenced via environment variable ${appVersion} inside of docker-compose.yaml.

3. To deploy recently built **weissbeerger-web** application run:

    ``
         export appVersion=[your version] && docker-compose up -d weissbeerger-web
    ``


    Example:
    ``
         export appVersion=v1 && docker-compose up -d weissbeerger-web
    ``

    You will also see the command example in the last pipeline print message from the previous step.
