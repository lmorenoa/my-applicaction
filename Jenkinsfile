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
        always {
            echo 'Post!!!'
        }    
        success{
            emailext subject: "Pipeline Successful", to: "lmalarza74@gmail.com"
        }
        unstable {
            emailext subject: "Pipeline unstable", to: "lmalarza74@gmail.com"
        }
        failure {
            emailext subject: "Pipeline Failure", to: "lmalarza74@gmail.com"
        }
    }
    
}
