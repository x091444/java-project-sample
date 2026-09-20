pipeline {
    agent {
        label "node1"
    }

    tools {
        maven "maven123"
    }

    options {
        skipDefaultCheckout(true)
    }

    stages {
        stage("clone") {
            steps {
                checkout scm
            }
        }

        stage("build") {
            steps {
                echo "build stage"
                sh "mvn clean package"
            }
        }

        stage("deploy") {
            steps {
                echo "deploy stage"
                sh """
                    cp /home/ubuntu/jenkins/workspace/sample/target/*.war /opt/tomcat/webapps/

                """
                dir("/opt/tomcat/webapps/"){
                    sh """
                        cp /opt/tomcat/webapps/java-tomcat-maven-example/* ROOT/
                    """
                }
                

            }
        }
        stage("cleanup") {
            steps {
                echo "cleanup stage"
                sh "rm -rf /opt/tomcat/webapps/java-tomcat-maven-example*"
            }
        }
    }
}