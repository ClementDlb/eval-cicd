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
        echo 'testing...'
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
        junit '**/target/surefire-reports/TEST-*.xml'
    }
  }
}