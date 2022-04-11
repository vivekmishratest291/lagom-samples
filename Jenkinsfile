ode('jenkins-slave') {

     stage('test pipeline') {
        sh(script: """
            echo "hello"
           git clone https://github.com/vivekmishratest291/lagom-samples.git
           cd ./mixed-persistence/mixed-persistence-scala-sbt/
           
           docker build . -t test
        """)
    }
}
