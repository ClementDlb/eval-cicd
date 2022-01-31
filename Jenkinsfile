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

    stage("publish"){
      steps {
        nexusArtifactUploader artifacts: [[artifactId: 'SimpleAstronomyLib', classifier: '', file: 'target/SimpleAstronomyLib-0.3.0.jar', type: 'jar']], credentialsId: 'nexus3', groupId: 'com.bradsbrain', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'eval-cicd', version: '0.3.0'
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