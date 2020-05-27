def dockerfilePath="/var/jenkins_home/docker-images/weissbeerger-web"

pipeline {
    
    agent any
    
    stages {
        stage("Build_docker_image") {
            steps {
                    script {
                        def applicationVersion="v${BUILD_NUMBER}"
                        def weissbeergerImage = docker.build("${appName}:${applicationVersion}", "${dockerfilePath}") 
                        //weissbeergerImage.push()
                        echo "${appName} application (version: ${applicationVersion}) successfully built."
                        echo "Run the following command to re-deploy it 'export appVersion=${applicationVersion} && docker-compose up -d weissbeerger-web'"
                    }
            }
        }
    }
}
