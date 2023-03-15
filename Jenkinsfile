//siri
pipeline {
    agent {label 'siri'} 
    stages {
        stage('vcs') { 
            steps {
                git url: 'https://github.com/shirishass/spc.git',
                branch: 'develop'
            } 
        }       
        stage('package') {
            steps {
                sh 'mvn package'
            }
        } 
        stage('post build') {
            steps {
                 archiveArtifacts artifacts: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
        }  
    }
}   
             


