pipeline{

    agent {
        label 'maven'
    }

    environment {
        EMAIL_TO = 'lmalarza74@gmail.com'
    }

    stages{      
         stage ('Build') {
                steps {
                    echo 'Building stage!!!'

                    sh 'rm -rf *'
                    checkout scm
   
                    // -- Compilando
                    echo 'Compilando aplicación'
                    sh 'mvn clean compile'

                }
            }
 
         stage ('Archive') {
                steps {
                    echo 'Archive stage!!!'
                    archiveArtifacts artifacts: '**/target/classes/*.*'
                }
            }


    }


    post {
        
        unstable {
            echo "Email to: ${EMAIL_TO} with: JOB NAME: ${env.JOB_NAME} BUILD_NUMBER: ${env.BUILD_NUMBER}"
            cleanWs()
        }
        failure {
            echo "Email to: ${EMAIL_TO} with: JOB NAME: ${env.JOB_NAME} BUILD_NUMBER: ${env.BUILD_NUMBER}"
            cleanWs()
        }
    }
    
}
