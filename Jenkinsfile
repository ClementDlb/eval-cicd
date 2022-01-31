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
        bat 'maven test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }

    stage("deploy"){

      steps {
        echo 'Deploying...'
      }
    }
  }
}