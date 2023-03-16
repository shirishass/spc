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
                name : 'spc'
                    includes: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar'
                }    
            }
        stage(collect file) {
            agent { label 'siri' }
            steps {
                name: 'spc'
            }
        } 
        stage('deployment') {
            agent { label 'siri' }
            steps {
                sh 'ansible-playbook -i hosts spc.yml'
            }
        }          
    }
}  
             


