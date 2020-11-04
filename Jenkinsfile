pipeline {
  agent any
  stages {
    stage('build') {
      when { not { branch 'master' } }
      steps {
        sh 'mvn compile'
      }
    }

    stage('test') {
      when { { branch 'master' } }
      steps {
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        sh 'mvn package -DskipTests'
        archiveArtifacts 'target/*.war'
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}