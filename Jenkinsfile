pipeline {
    agent any
    
    environment {
        registry = "vivekdevopsfree/tom"
        dockerImage = ""
    }
    
    tools {
        maven 'mymaven'
    }
    
    stages {
        stage('Get code') {
            steps {
                git 'https://github.com/Vivek-jayachandran/vanakkam-world'
            }
        }
        
        stage('Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Build image') {
            steps {
                script {
                    dockerImage = docker.build(registry + ":$BUILD_NUMBER")
                }
            }
        }
        stage('Push image to Docker registry') {
    steps {
        script {
            withRegistry('https://index.docker.io/v1/', credentialsId: "322f574f-2de4-4835-82f9-476615b381e5") {
                dockerImage.push()
            }
        }
    }
}
    }
}
