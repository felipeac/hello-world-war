pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                withMaven ( maven: 'Maven 3.5.3',
                    options: [ artifactsPublisher(disabled: true) ]
                ) {
                    sh "mvn clean package"
                }
            }
        }
        stage ('Deploy') {
            steps {
                sh 'curl --upload-file target/*.war "http://tomcat-admin:tomcat-admin@172.17.0.3:8080/manager/text/deploy?path=/hello-world&update=true"'
            }
        }
    }
}
