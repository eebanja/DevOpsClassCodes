pipeline {
    agent none

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        jdk "manJAVA"
        maven "autoMAVEN"
    }

    stages {
        stage('Compile') {
            agent any
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/eebanja/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn compile"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }

        stage('CodeReview') {
            agent any
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/eebanja/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn pmd:pmd"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
            
        stage('UnitTest') {
            agent any
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/eebanja/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn test"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
            
        stage('MetricCheck') {
            agent any
            steps {
                // Get some code from a GitHub repository
                // git 'https://github.com/eebanja/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn cobertura:cobertura -Dcobertura.report.format=xml"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
            
        stage('Package') {
            agent {label 'awsJenkinsAgent1'}
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/eebanja/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn package"

                // To run Maven on a Windows agent, use
                // bat "mvn -Dmaven.test.failure.ignore=true clean package"
            }
        }
    }
}
