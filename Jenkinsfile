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
                withMaven   (options: [jacocoPublisher(disabled: true)]) {
                    sh 'mvn clean verify'
                 }
            }
        }
    }
    post {
        always {
            jacoco(execPattern: '**/*.exec')
        }
    }
}
