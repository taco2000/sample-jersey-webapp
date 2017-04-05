pipeline {
    agent any
    stages {
        stage ("Compile") {
            steps {
                sh "mvn clean compile"
            }
            
        }

        stage ("Unit Test") {
            steps {
                sh "mvn test"
            }
        }
    }
}