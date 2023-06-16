pipeline{

    agent {
        label 'maven'
    }


    stages{      
         stage ('Build') {
                steps {
                    echo 'Building stage!!! '

                    sh 'rm -rf *'
                    checkout scm
   
                    // -- Compilando
                    echo 'Compilando aplicación'
                    sh 'mvn clean compile'
                    sh 'ls target/classes'
                    sh 'pwd'
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
            echo 'AWS S3!!!'
            withAWS(region:'eu-west-2', credentials: 'aws-default'){
			s3Upload(bucket:'my-aplis374', file: 'target/classes/*.*')
		    }

            echo 'Email Successful !!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Successful",
            body: "Revision exitosa para el nodo ${env.NODE_NAME} sobre el build ${env.BUILD_NUMBER} en la tarea ${env.JOB_NAME} "
        }
        failure {
            echo 'Email Error !!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Error",
            body: "Revision erronea para el nodo ${env.NODE_NAME} sobre el build ${env.BUILD_NUMBER} en la tarea ${env.JOB_NAME} "
        }
    }
    
}
