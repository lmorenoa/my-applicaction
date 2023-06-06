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
            echo 'Successful!!!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Successful",
            body: "Text"
        }
        failure {
            echo 'Error!!!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Error",
            body: "Text"
        }
    }
    
}
