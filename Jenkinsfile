node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven3.8.7';
    if(env.BRANCH_NAME==~ /^PR-\d+$/){
        withSonarQubeEnv('SonarQubeScanner-4.6.2'){
            sh "${scannerHome}/bin/sonar-scanner" +
            "-Dsonar.pullrequest.key=$CHANGE_ID " +
            "-Dsonar.pullrequest.branch=$CHANGE_BRANCH " +
            "-Dsonar.pullrequest.base=$CHANGE_TARGET"

        }
    }else {
         echo " working  "
    }
  }
}