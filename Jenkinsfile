pipeline{

    agent {
        label 'maven'
    }

    environment {
        EMAIL_TO = 'mariofont@icloud.com'
    }

    stages{      
         stage ('Build') {
                steps {
                    echo 'Building stage!'

                    sh 'rm -rf *'
                    checkout scm
   
                    // -- Compilando
                    echo 'Compilando aplicación'
                    sh 'mvn clean compile'

                }
            }
 
         stage ('Archive') {
                steps {
                    echo 'Archive stage!'
                    archiveArtifacts artifacts: '*.jar'
                }
            }


    }
    
}
