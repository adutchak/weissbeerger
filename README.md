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

Default parameters already matching image name&version references in **docker-compose.yaml**. 
However, you can specify a different image name & version.

If you change the image name or version in Jenkins don't forget to change it in the docker-compose.yaml too.

3. Start recently built **weissbeerger-web** application by running:

    ``
         docker-compose up -d weissbeerger-jenkins
    ``