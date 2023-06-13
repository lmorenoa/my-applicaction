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
            withAWS(region:'us-east-1', credentials: 'aws-default'){
			s3UpLoad(bucket:'my-aplis3', file: 'target/classes/application.properties')
		    }

            echo 'Email!!!'
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
