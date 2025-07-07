pipeline {
    agent any

    stages {
        stage("Build") {
            steps {
                sh ```
                    #!/bin/bash -xe
                    mvn compile
                ```
            }
        }

        stage("Test") {
            steps {
                wrap([$class: "Xvfb", debug: true, autoDisplayName: true]) {
                    sh ```
                        #!/bin/bash -xe
                        mvn test
                    ```
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
