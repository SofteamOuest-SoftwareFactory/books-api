pipeline {
    agent {
        docker {
            image 'maven:3.6.1'
            args '-v $HOME/.m2:/root/.m2'
            label 'slave-amf'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
    }

    post {
            failure {
                // send to email
                emailext(
                        subject: "FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                        body: """<p>FAILURE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                 <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                )
            }
            unstable {
                // send to email
                emailext(
                        subject: "UNSTABLE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                        body: """<p>UNSTABLE: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
                 <p>Check console output at "<a href="${env.BUILD_URL}">${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']]
                )
            }
        }
}