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
                sh 'curl --upload-file target/hello-world-war-1.0.0.war "http://tomcat-admin:tomcat-admin@localhost:8888/manager/text/deploy?path=/hello-world&update=true"'
            }
        }
    }
}
