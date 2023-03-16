pipeline {
    agent {label 'siri'} 
        triggers { pollSCM ('* * * * *') }
    stages {
        stage('vcs') { 
            steps {
                git url: 'https://github.com/shirishass/spc.git',
                branch: 'release'
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
                stash name: 'spc'
                      includes: '**/target/spring-petclinic-3.0.0-SNAPSHOT.jar'
                }    
            }
        stage('collect file') {
            agent { label 'siri' }
            steps {
                unstash name: 'spc'
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
             


