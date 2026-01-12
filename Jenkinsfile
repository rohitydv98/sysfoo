pipeline {
  agent any
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
        sh '''# Truncate the GIT_COMMIT to the first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)
# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -Dskiptests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}