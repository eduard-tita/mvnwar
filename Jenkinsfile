pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn --batch-mode -V -U clean verify'
            }
        }
        stage('Deploy-release') {
            steps {
                nexusPublisher
                  nexusInstanceId: 'local-nexus-3',
                  nexusRepositoryId: 'et-maven-releases',
                  packages: [[$class: 'MavenPackage',
                    mavenAssetList: [[classifier: '',
                      extension: '',
                      filePath: '/home/eduard/.jenkins/workspace/Mvnwar Pipeline/target/mvnwar-1.1.war']],
                      mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: '1.1']]]
            }
        }
    }
}

