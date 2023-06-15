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
                    sh 'cd target/classes'
                    sh 'pwd'
                    sh 'ls'
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
			s3Upload(bucket:'my-aplis374', file: 'target/classes/application.properties')
		    }

            echo 'Email Successful !!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Successful",
            body: "Text"
        }
        failure {
            echo 'Email Error !!'
            emailext to: "lmalarza74@gmail.com",
            subject: "Pipeline Error",
            body: "Text"
        }
    }
    
}
