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
}
