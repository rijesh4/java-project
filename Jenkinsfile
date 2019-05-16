node ('linux') {
  stage('Unit Tests') {
    git 'https://github.com/rijesh4/java-project.git'
    sh 'ant -f test.xml -v'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Deploy') {
    sh 'aws s3 cp /workspace/infra/dist/rectangle-$BUILD_NUMBER.jar s3://kuma5739-assignment10-devops/'
  }
  stage('Report') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '67367deb-42c5-401b-b97e-e4378ac2e8e7', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
  }
}
