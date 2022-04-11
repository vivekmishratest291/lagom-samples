node('jenkins-slave') {
    
     stage('test pipeline') {
        sh(script: """
            echo "hello"
           git clone https://github.com/vivekmishratest291/lagom-samples.git
           cd ./lagom-samples/couchbase-persistence/docker/
          /opt/java/openjdk/bin/java -Dsbt.log.noformat=true -jar /var/jenkins_home/sbt-0.3.8/sbt-launch.jar docker:publishLocal
        """)
    }
}
