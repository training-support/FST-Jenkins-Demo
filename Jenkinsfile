pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                sh "mvn compile"
            }
        }

        stage("Test") {
            steps {
                wrap([$class: "Xvfb", debug: true, autoDisplayName: true]) {
                    sh "mvn test"
                }
            }
        }

        stage("Publish") {
            steps {
                testNG()
            }
        }
    }
}
