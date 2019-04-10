pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -V -U clean verify'
        //nexusPolicyEvaluation failBuildOnNetworkError: false, iqApplication: selectedApplication('et-hw'), iqStage: 'build', jobCredentialsId: ''
      }
    }
    stage('Deploy-release') {
      steps {
        def project.version='1.3'
        echo "project.version: ${projectVersion}"

        nexusPolicyEvaluation failBuildOnNetworkError: false, iqApplication: selectedApplication('et-hw'), iqStage: 'release', jobCredentialsId: ''

        nexusPublisher nexusInstanceId: 'local-nexus-3', nexusRepositoryId: 'et-maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: "/home/eduard/.jenkins/workspace/Mvnwar Release/target/mvnwar-${projectVersion}.war"]], mavenCoordinate: [artifactId: 'mvnwar', groupId: 'ca.oscinc.mvnweb', packaging: 'war', version: "${projectVersion}"]]]
      }
    }
  }
}

