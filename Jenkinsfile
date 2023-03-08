pipeline {
    agent {label 'openmrs'}
    tools { maven 'MAVEN_3.6.3'
            jdk 'JDK_17'}
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