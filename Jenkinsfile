node('UBUNTU_NODE3') {
    stage('vcs') {
        git url: 'https://github.com/srikanthvelma/openmrs-core.git',
            branch: 'scripted'
    }
    stage('build') {
        sh "export 'PATH=/usr/lib/jvm/java-1.8.0-openjdk-amd64/bin:$PATH'"
        sh 'mvn package'
    }
    stage('post build') {
        archiveArtifacts artifacts: '**/target/openmrs-liquibase-2.7.0-SNAPSHOT-tests.jar'
                         junit '**/surefire-reports/TEST-*.xml'
    }
}