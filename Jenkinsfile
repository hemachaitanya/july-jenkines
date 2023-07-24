pipeline {
    agent { label 'EEE'}
    triggers {
        pollSCM('* * * * *')
    }
     stages {
        stage('vcs'){
            steps {
                git url: 'https://github.com/hemachaitanya/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage(build){
            steps{
                sh 'mvn clean package'
            }   
        }
        stage('nexus') {
            steps{
                nexusArtifactUploader artifacts: [[artifactId: 'spring-petclinic', classifier: '', file: '/home/ubuntu/workspace/job-nexus/target/spring-petclinic-3.0.0-SNAPSHOT.jar', type: 'jar']], credentialsId: 'NEXUS', groupId: 'org.springframework.samples', nexusUrl: '3.83.1.163:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'maven-snapshots', version: '3.0.0-SNAPSHOT'
            }    
        }
    }
}



   
