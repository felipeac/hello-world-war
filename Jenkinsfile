pipeline {
    agent any
    stages {
        stage ('Build') {
            withMaven ( maven: 'Maven 3.5.3',
                options: [ artifactsPublisher(disabled: true) ]
            ) {
                sh "mvn clean package"
            }
        }
        stage ('Deploy') {
            echo  'deploy'
        }
    }
}
