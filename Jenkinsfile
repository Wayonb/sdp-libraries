node{
  stage("Unit Test"){
    checkout scm
     sh "docker build -f unit_test.Dockerfile -t pipeline-unit-testing ."
    // sh "docker run --rm -t -v \$(pwd):/app -w /app pipeline-unit-testing gradle --no-daemon test"
    // sh "JAVA_HOME=\'/usr/lib/jvm/java-1.8-openjdk/\' && ./gradlew test"

    docker.image("pipeline-unit-testing").inside{
      sh "gradle --no-daemon clean test"
    }
    archiveArtifacts artifacts: 'target/reports/tests/test/**'

  }
}
