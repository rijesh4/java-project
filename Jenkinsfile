node ('linux') {
  stage('Unit Test') {
    git 'https://github.com/rijesh4/java-project.git'
    sh 'ant -f test.xml -v'
  }
  stage('Build') {
    sh 'ant -f build.xml -v'
  }
}
