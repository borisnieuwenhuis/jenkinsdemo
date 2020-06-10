pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                withMaven {
                    sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=sonar:test -Dsonar.host.url=http://localhost:9000 -Dsonar.login=7b644d23c2a93b4d3cf21c95a485f1cf2acf41c6'
                 }
            }
        }
    }
}
