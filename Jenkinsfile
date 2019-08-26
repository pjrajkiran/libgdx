pipeline {
  agent any
  tools {
    maven "Maven"
  }
  stages {
      stage("Build") {
          steps {
              echo "Building"
              snDevOpsStep '8bc34a2bdbd3330070a8ff9dbf9619be'
              sh 'mvn clean install'
          }
      }
      stage("Test") {
           steps {
                echo "Testing"
                snDevOpsStep '0fc34a2bdbd3330070a8ff9dbf9619be'
                sh 'mvn test -Dpublish'
                junit '**/target/surefire-reports/*.xml'
           }
       }
       stage("UAT Test") {
           steps {
                snDevOpsStep '8fc34a2bdbd3330070a8ff9dbf9619be'
                echo "UAT Testing"
                sh 'mvn test -Dpublish'
                junit '**/target/surefire-reports/*.xml'
           }
       }
      stage("Deploy") {
          steps {
            snDevOpsStep '83c34a2bdbd3330070a8ff9dbf9619be'
            sh 'mvn test -Dpublish'
            junit '**/target/surefire-reports/*.xml'
          }
      }
  }
}