pipeline {
  agent any
  tools {
    maven "Jenkins Maven"
  }
  stages {
      stage("Build") {
          steps {
            echo 'build .....'
              snDevOpsStep '8bc34a2bdbd3330070a8ff9dbf9619be'
              sh 'mvn clean install'
          }
      }
      stage("Test") {
           steps {
             echo 'test ......'
                snDevOpsStep '0fc34a2bdbd3330070a8ff9dbf9619be'
                //snDevOpsChange()
                sh 'mvn test -Dpublish'
                junit '**/target/surefire-reports/*.xml'
           }
       }
       stage("UAT Test") {
           steps {
             echo 'UAT ....'
                snDevOpsStep '8fc34a2bdbd3330070a8ff9dbf9619be'
                //snDevOpsChange()
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
