pipeline {
    agent { label 'EEE'}
    triggers {
        pollSCM('* * * * *')
    }
    tools {
        jdk 'JDK-17'
    }
     stages {
        stage('vcs'){
            steps {
                git url: 'https://github.com/hemachaitanya/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage ('build'){
            steps {
                sh 'mvn clean install'
            }
        }
    }   
}

   
