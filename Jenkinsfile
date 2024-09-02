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
            branch 'master'
            stage('Sast & Oss') {
                if (parameters.Release_PSI == true) {
                    stage('Sast') {
                        steps {
                            echo 'Sast'
                        }
                    }
                    stage('Oss') {
                        steps {
                            echo 'Oss'
                        }
                    }
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
