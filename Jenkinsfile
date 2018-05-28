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
                echo $WORKSPACE
                sh 'curl --upload-file ${WORKSPACE}/target/hello-world.war "http://tomcat-admin:tomcat-admin@localhost:8888/manager/text/deploy?path=/hello-world&update=true"'
            }
        }
    }
}
