pipeline {
  agent any
  tools {
    maven "Jenkins Maven"
  }
  stages {
      stage("Build") {
          steps {
            echo 'build ....'
              snDevOpsStep '42500b74db6bf300106254c0cf9619b7'
              sh 'mvn clean install'
          }
      }
      stage("Test") {
           steps {
             echo 'test .....'
                snDevOpsStep 'c2500b74db6bf300106254c0cf9619b7'
                snDevOpsChange()
                sh 'mvn test -Dpublish'
                junit '**/target/surefire-reports/*.xml'
           }
       }
       stage("UAT Test") {
           steps {
             echo 'UAT .......'
                snDevOpsStep '46500b74db6bf300106254c0cf9619b7'
                snDevOpsChange()
                sh 'mvn test -Dpublish'
                junit '**/target/surefire-reports/*.xml'
           }
       }
      stage("Deploy") {
          steps {
            snDevOpsStep '4a500b74db6bf300106254c0cf9619b6'
            sh 'mvn test -Dpublish'
            junit '**/target/surefire-reports/*.xml'
          }
      }
  }
}
