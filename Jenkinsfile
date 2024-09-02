pipeline {
    agent any

    parameters {
        booleanParam(name: 'Release_PSI', defaultValue: true, description: 'Scanning Sast & Oss')
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Start SAST') {
            when {
                branch 'master/*'
                allOf {
                    environment name: 'Release_PSI', value: true
                }
            }
            steps {
                echo 'Start Sast'
            }
        }

        stage('Start OSS') {
            when {
                branch 'master/*'
                allOf {
                    environment name: 'Release_PSI', value: true
                }
            }
            steps {
                echo 'Start Oss'
            }
        }

        stage('Deploy IFT') {
            steps {
                echo 'Deploy IFT'
            }
        }

    }
}
