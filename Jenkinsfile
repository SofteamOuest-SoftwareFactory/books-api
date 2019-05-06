#!groovy
import java.text.*

node('any') {

    properties([
            buildDiscarder(
                    logRotator(
                            artifactDaysToKeepStr: '1',
                            artifactNumToKeepStr: '1',
                            daysToKeepStr: '3',
                            numToKeepStr: '3'
                    )),
            pipelineTriggers([pollSCM('*/1 * * * *')])
    ])

    stage('CHECKOUT') {
        checkout scm
    }


    stage('BUILD') {


    }
}
