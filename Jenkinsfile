pipeline {
    agent any

    tools {
      maven 'Maven 3.9.6'
    }
    stages {
        stage('build') {
            steps {
                echo 'compile'
                sh 'mvn compile'
            }
        }

        stage('build unit test') {
            steps {
                echo 'test'
                sh 'mvn clean test'
            }
        }

        stage('build package jo') {
            steps {
                echo 'package'
                sh 'mvn package -Dskiptests'
            }
        }
    }

    post {
        always {
            echo 'This pipeline is completed..'
        }
    }
}
