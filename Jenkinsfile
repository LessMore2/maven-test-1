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
            if (branch.isMaster() && params.Release_PSI == true) {
                steps {
                    echo 'Start Sast & Oss_2'
                }
            }
        }

        stage('Deploy IFT') {
            steps {
                echo 'Deploy IFT'
            }
        }

    }
}
