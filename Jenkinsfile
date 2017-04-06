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
                step{sh "mvn test"}
                step{[$class: 'JUnitResultArchiver', testDataPublishers: [[$class: 'AttachmentPublisher']], testResults: 'test/*.xml']}
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

        if (BRANCH_NAME == 'master') {
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
        }
    }
}