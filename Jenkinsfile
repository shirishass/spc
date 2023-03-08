pipeline {
    agent {label 'openmrs'}
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/sirijenkins/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
            }
        }        
       // stage('sonar analysis') {
                // requires SonarQube Scanner for Maven 3.2+
                //sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
         //   steps {
        //        }   
         //  }    
      //  }
    }  
} 