pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean verify'
            }
        }
        stage('Deploy') {
            steps {
                nexusPublisher nexusInstanceId: 'local-nexus-3', nexusRepositoryId: 'et-hosted-release', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/home/eduard/.jenkins/workspace/Mvnwar Pipeline/target/mvnwar-1.0.war']], mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: '1.0']]]
            }
        }
    }
}

