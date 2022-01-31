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
}