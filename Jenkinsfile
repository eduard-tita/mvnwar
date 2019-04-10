pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -V -U clean verify'
            }
        }
        stage('Deploy-release') {
            steps {
                nexusPublisher nexusInstanceId: 'local-nexus-3', nexusRepositoryId: 'et-maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/home/eduard/.jenkins/workspace/Mvnwar Release/target/mvnwar-1.2.war']], mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: '1.2']]]
            }
        }
    }
}

