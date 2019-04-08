pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn --batch-mode -V -U clean verify'
            }
        }
//        stage('Deploy-snapshot') {
//            steps {
//                nexusPublisher nexusInstanceId: 'local-nexus-3', nexusRepositoryId: 'et-maven-snapshots', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target/mvnwar-1.0-SNAPSHOT.war']], mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: '1.0-SNAPSHOT']]]
//            }
//        }
        stage('Deploy-release') {
            steps {
                nexusPublisher nexusInstanceId: 'local-nexus-3', nexusRepositoryId: 'et-hosted-release', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '/home/eduard/.jenkins/workspace/Mvnwar Pipeline/target/mvnwar-1.1.war']], mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: '1.1']]]
            }
        }
    }
}

