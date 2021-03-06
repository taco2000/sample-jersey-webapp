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
                junit allowEmptyResults: true, testResults: 'test/*.xml'
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

        stage ("Bump Release Version") {
            when {
                expression {return BRANCH_NAME == "master" }
            }
            steps {
                echo "Bumping release version"
            }
        }

        stage ("Update changelog") {
            when {
                expression {return BRANCH_NAME == "master" }
            }            
            steps{
                echo "Updating changelog"
            }
        }
        stage ("Publish release artifacts") {
            when {
                expression {return BRANCH_NAME == "master" }
            }            
            steps{
                echo "Publish release artifacts"
            }
        }
    }
}