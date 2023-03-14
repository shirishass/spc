//siri
pipeline {
    agent {label 'siri'} 
    stages {
        stage('Build') { 
            steps {
                git url: 'https://github.com/shirishass/spc.git',
                branch: 'develop'
            } 
        }       
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }    
    }
}   
             


