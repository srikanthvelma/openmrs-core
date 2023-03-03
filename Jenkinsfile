pipeline {
    agent { label 'UBUNTU_NODE3' }
    stages{
        stage('vcs') {
            steps{
                git url: 'https://github.com/srikanthvelma/openmrs-core.git',
                    branch: declarative
            }
        }
        stage('build') {
            steps{
                sh "export 'PATH=/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH'"
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps{
                archiveArtifact artifacts: '**/target/openmrs-liquibase-2.7.0-SNAPSHOT-tests.jar'
                                junit '**/surefire-reports/TEST-*.xml'
             }
        }
    }
}
    
