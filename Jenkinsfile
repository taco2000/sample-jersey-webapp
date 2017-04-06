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
                //junit '*/target/surefire-reports/*.xml'
                //junit allowEmptyResults: true, testResults: 'test/*.xml'
                //step([$class: 'JUnitResultArchiver', testDataPublishers: [[$class: 'AttachmentPublisher']], testResults: 'test/*.xml'])
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
    }

    /*
    // Perform a release if on the master branch
    stages {
        stage ("Bump Release Version") {
            steps{
                echo "Bumping release version"
            }
        }
        stage ("Update changelog") {
            steps{
                echo "Updating changelog"
            }
        }
        stage ("Publish release artifacts") {
            steps{
                echo "Publish release artifacts"
            }
        }
    } when {
        return BRANCH_NAME == "master"
    }*/
}