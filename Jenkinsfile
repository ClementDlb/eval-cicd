pipeline {
  agent any

  stages {
    stage("build"){

      steps {
        bat 'mvn clean package'
      }
    }

    stage("test"){

      steps {
        bat 'mvn test'
      }
    }

    stage("deploy"){

      steps {
        echo 'Deploying...'
      }
    }
  }

  post {
    success {
        archiveArtifacts 'target/*.jar'
    }
    always {
        junit '**/target/surefire-reports/TEST-*.xml'
    }
  }
}