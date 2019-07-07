node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/aashishprabhakaran/maven_apps.git'
   }
   stage('Build code') {
      echo 'Build the package'
      withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn clean compile'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
             //sh 'mvn clean package sonar:sonar' 
             sh ' mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar ' +
             ' -Dsonar.host.url=https://sonarcloud.io ' +
             ' -Dsonar.organization=aashishprabhakaran-github ' +
             ' -Dsonar.login=ac9d4e50459a71a808e9d31a2448987f4998ff1d '   
         //}
      }
   }
    
    
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'JDK-1.8', maven: 'Maven-3.6.1') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
   stage('Deploy to Prod'){
       echo 'Deploy to Prod environment'
   }
      
   
}
