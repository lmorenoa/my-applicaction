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
                    sh 'mvn'
                }
            }
 
         stage ('Archive') {
                steps {
                    echo 'Archive stage!'
                    archiveArtifacts artifacts: 'target/*.jar'
                }
            }


    }
    
}
