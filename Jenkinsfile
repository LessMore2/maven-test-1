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

        stage('Sast & Oss') {
            when {
                branch.isMaster()
                environment name: 'Release_PSI', value: true
            }
            steps {
                echo 'Start Sast & Oss'
            }
        }

        stage('Deploy IFT') {
            steps {
                echo 'Deploy IFT'
            }
        }

    }
}
