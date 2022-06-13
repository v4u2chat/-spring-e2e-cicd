pipeline {
    agent any
    tools { 
      maven 'M2_HOME' 
      jdk 'JDK11' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }

        stage ('Build') {
            steps {
                git url: 'https://github.com/v4u2chat/spring-e2e-cicd.git'
                withMaven(){
                    sh 'mvn clean package'    
                }
                 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }
    }
}