pipeline {
  agent any
    stages {
      stage('Build') {
        steps {
          awsCodeBuild projectName: 'CodeBuildDemo',
                       credentialsId: 'codebuild-id',
                       credentialsType: 'jenkins',
                       region: 'us-east-1',
                       sourceControlType: 'project'

        }
      }
    }
}
