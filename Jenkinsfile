node ('linux') {
  stage('Unit Tests') {
    git 'https://github.com/rijesh4/java-project.git'
    sh 'ant -f test.xml -v'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
  stage('Deploy') {
    sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-$BUILD_NUMBER.jar s3://kuma5739-assignment10-devops/'
  }
  stage('Report') {
    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'bddef3c1-a56a-4cbd-be00-ab76b7960f04', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
      sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
    }
  }
}
