pipeline{
    agent {
        label "node1"
    }
    tools{
        maven "maven123"
    }
    options{
        skipdefaultCheckout(true)
    }

    stages{
        stage("clone"){
            steps{
                checkout scm
            }
        }
        stage("build"){
            steps{
                echo "build stage"
                sh "mvn clean package"
            }
        }
        stage("deploy"){
            steps{
                echo "deploy stage"
            }
        }
    }
}
