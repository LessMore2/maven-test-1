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

        when {
            expression {
                branch 'master/*'
                params.Release_PSI == true
            }
        }
        steps {
            startStat()
        }

        stage('Start OSS') {
            when {
                expression {
                    branch 'master/*'
                    params.Release_PSI == true
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

def startStat() {
    stage('Starting Sast') {
        steps {
            echo 'Start Oss'
        }
    }
}
