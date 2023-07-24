pipeline {
    agent any
     stages {
        stage('vcs'){
            steps {
                git url: 'https://github.com/hemachaitanya/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage ('build'){
            steps {
                sh 'cd spring-petclinic && mvn clean install'
            }
        }
    }
   
        
    }
   
