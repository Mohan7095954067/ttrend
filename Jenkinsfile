pipeline {
    agent {
        node{
            label 'maven'
        }
    }
environment {
    PATH = "/opt/maven/bin:$PATH"
}    

    stages {
        stage('build'){
            steps{
                sh 'mvn clean install'
            }
        } 
    
        stage('SonarQube analysis') {
        environment {
        scannerHome = tool 'valaxy-sonar-scanner'
          }
          steps{
          withSonarQubeEnv('valaxy-sonarqube-server') { 
          sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }
}   
}

