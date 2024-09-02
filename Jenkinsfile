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
                expression {
                    env.BRANCH_NAME == "master/*" && params.Release_PSI == true
                }
            }
            steps {
                echo 'Start Sast'
            }
        }

        stage('Start OSS') {
            when {
                expression {
                    env.BRANCH_NAME == "master/*" && params.Release_PSI == true
                }
            }
            steps {
                echo 'Start Oss'
            }
        }

//        stage('Sast & Oss') {
//            when {
//                expression {
//                    branch 'master/*'
//                    params.Release_PSI == true
//                }
//            }
//
//            steps {
//                echo 'Start Sast & Oss_2'
//            }
//        }

        stage('Deploy IFT') {
            steps {
                echo 'Deploy IFT'
            }
        }

    }
}
