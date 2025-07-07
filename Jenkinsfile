pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                sh '''
                #!/bin/bash
                set +e
                set +x
                mvn compile
                '''
            }
        }

        stage("Test") {
            steps {
                wrap([$class: "Xvfb", debug: true, autoDisplayName: true]) {
                    sh '''
                    #!/bin/bash
                    set +e
                    set +x
                    mvn test
                    '''
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
