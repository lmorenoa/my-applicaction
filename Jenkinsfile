pipeline{

    agent {
        label 'principal'
    }

    environment {
        EMAIL_TO = 'mariofont@icloud.com'
    }

    stages{      
        stage('Run tests') {

            stage ('Build') {
                steps {
                    echo 'Building stage!'
                    sh 'mvn'
                }
            }
 
    }
    
}
}
