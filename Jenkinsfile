pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'mvn clean test'
            }
        }
        stage('Build') {
            steps {
               sh '''
               mvn clean install
               mkdir -p/home/jenkins/projest-wars
               mv ./target/*.war /home/jenkins/project-wars/project-${BUILD_NUMBER}.war
               '''
            }
        }
        stage('Deploy') {
            steps {
              sh '''
              nohup java -jar /home/jenkins/project-wars/project-${BUILD_NUMBER}.war &
              '''
            }
        }
    }
}