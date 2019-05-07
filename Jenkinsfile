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
}