pipeline {
    agent any

    stages {
        stage('Build') {
       stage('SCM') {
    git 'https://github.com/foo/bar.git'
  }
  stage('SonarQube analysis') {
    withSonarQubeEnv(credentialsId: 'f225455e-ea59-40fa-8af7-08176e86507a', installationName: 'My SonarQube Server') { // You can override the credential to be used
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
  }
}
        }
        stage('Deploy') {
           rtServer (
    id: 'Artifactory-1',
    url: 'http://my-artifactory-domain/artifactory',
    // If you're using username and password:
    username: 'user',
    password: 'password',
    // If you're using Credentials ID:
    credentialsId: 'ccrreeddeennttiiaall',
    // If Jenkins is configured to use an http proxy, you can bypass the proxy when using this Artifactory server:
    bypassProxy: true,
    // Configure the connection timeout (in seconds).
    // The default value (if not configured) is 300 seconds:
    timeout: 300
)
    }
}

