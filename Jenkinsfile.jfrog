pipeline{
    agent{ label 'EEE'}
    tools{
        jdk 'JDK-17'
        maven 'MVN-3.9'
    }
    stages {
        stage ('git clone'){
            steps{
                git url: 'https://github.com/spring-projects/spring-petclinic.git',
                    branch: 'main'
            }
        }
        stage ('jfrog') {
            steps{
                rtMavenDeployer (
                    id: 'maven-deployer',
                    serverId: JFROG-CURD,
                    releaseRepo: 'chaitu-libs-release',
                    snapshotRepo: 'chaitu-libs-snapshot'
                )
                 rtMavenRun (
                    tool: 'MVN-3.9',
                    pom: 'pom.xml',
                    goals: '-U clean install',
                    deployerId: "maven-deployer"
                )
                 rtPublishBuildInfo (
                    serverId: "JFROG-CURD"
                )
            }

        }
    }
}