pipeline {
    agent {label 'openmrs'}
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/sirijenkins/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }        
        stage('sonar analysis') {
            steps {
                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR') {
                    sh 'mvn clean package sonar:sonar -Dsonar.organization=shirisha'
                }
            } 
       }    
    }
}        