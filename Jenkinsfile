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

        stage("Static Analysis") {
            steps {
                sh "mvn pmd:pmd findbugs:findbugs"
            }
        }

        stage ("Package") {
            steps {
                sh "mvn package"
            }
        }
    }
}