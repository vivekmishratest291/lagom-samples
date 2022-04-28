node {
    stage('SBT compile*****') {
        dir('./shopping-cart/shopping-cart-scala') {
        sh "pwd"
  sh "/usr/lib/jvm/java-11-openjdk-amd64/bin/java -jar /home/mishra/sbt-dist/bin/sbt-launch.jar clean compile"
        }
  }
  stage('SCM') {
    checkout scm
      sh "pwd"
  }
  stage('SonarQube Analysis') {
        dir('./shopping-cart/shopping-cart-scala') {
    def scannerHome = tool 'SonarScanner';
      sh "pwd"
    withSonarQubeEnv('lagom-sonar') {
      sh "${scannerHome}/bin/sonar-scanner \
  -Dsonar.projectKey=lagom-sonar \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://localhost:9002/sonarqube \
  -Dsonar.login=6766834c610f233898a2c035364ed28e33b390c1"
    }
  }
  }
}
stage("Quality Gate"){
  timeout(time: 1, unit: 'HOURS') { // Just in case something goes wrong, pipeline will be killed after a timeout
    def qg = waitForQualityGate() // Reuse taskId previously collected by withSonarQubeEnv
    if (qg.status != 'OK') {
      error "Pipeline aborted due to quality gate failure: ${qg.status}"
    }
  }
}
