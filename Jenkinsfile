pipeline {
    agent any
    stages{
        stage('Build'){
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
        stage ('Deploy to Staging'){
            steps {
                build job: 'lesson-1-first-jenkins-job'
            }
        }

         stage ('Deployments') {
         parallel{
           stage ('Deploy to Staging'){
             steps {
               build job: 'lesson-1-first-jenkins-job'
             }
           }
           stage ('Deploy to prod') {
             steps {
               build job: 'lesson-1-first-jenkins-job'
             }     
           }
         }
       }
    }
}
