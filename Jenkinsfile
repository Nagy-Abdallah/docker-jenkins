pipeline {
   agent any
    environment {
        DEOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage('CodeClone'){
            steps {
                git credentialsId: 'githibPassword', url: 'https://github.com/Nagy-Abdallah/docker-jenkins.git'
            }
        }
        stage('BUILD'){
            steps {
                sh 'docker build -t nagyadel/jenkins_iti:${BUILD_NUMBER} .'
            }
        }
        stage('Login'){
            steps { 
                sh 'echo $DEOCKERHUB_CREDENTIALS_PSW | docker login -u  $DEOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'echo LogedIn successfully!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!'
            }
        }
        stage('PUSH'){
            steps {
                sh 'docker push nagyadel/jenkins_iti:${BUILD_NUMBER}'
            }
        }
        
        
    }
}
