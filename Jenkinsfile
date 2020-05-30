pipeline {
    
    agent any
    
    stages {
        stage("Build_docker_image") {
            steps {
                    checkout([$class: 'GitSCM', 
                              branches: [[name: '*/${codeVersion}']], 
                              doGenerateSubmoduleConfigurations: false, 
                              extensions: [], 
                              submoduleCfg: [], 
                              userRemoteConfigs: [[url: '${repo}']]])
                    
                    script {
                        def applicationVersion="v${BUILD_NUMBER}"
                        def weissbeergerImage = docker.build("${appName}:${applicationVersion}", "./docker-images/${appName}") 
                        //weissbeergerImage.push()
                        echo "${appName} application (version: ${applicationVersion}) successfully built."
                        echo "Run the following command to re-deploy it 'export appVersion=${applicationVersion} && docker-compose up -d weissbeerger-web'"
                    }
            }
        }
    }
}