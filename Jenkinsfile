#!/usr/bin/env groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper
import hudson.AbortException
@Library('profilev2-jenkins-shared-libraries') _

def label = "mypod-${UUID.randomUUID().toString()}"

podTemplate(label: label,
        containers: [
                // pod container template is for the infrastructure launch and application deployment
                containerTemplate(name: 'docker-infrastructure-deployment',
                        image: 'docker.artifactory.a.intuit.com/dev/build/ibp/ibp-infrav2-admin-service:latest',
                        ttyEnabled: true,
                        command: 'cat',
                        args: '',
                        alwaysPullImage: true,
                ),
                containerTemplate(name: 'docker-maven-jdk-build',
                        image: 'docker.artifactory.a.intuit.com/dev/build/ibp/ibp-npm-fpm-bash:1.1',
                        ttyEnabled: true,
                        command: 'cat',
                        args: '',
                        alwaysPullImage: true,
                ),
                containerTemplate(name: 'docker-aws-cli',
                        image: 'docker.artifactory.a.intuit.com/dev/build/ibp/ibp-aws-cli:1.1',
                        ttyEnabled: true,
                        command: 'cat',
                        args: '',
                        alwaysPullImage: true,
                )
        ]
)


{
node(label) {
//pipeline {
//  agent any
        stage('pre script') {
            echo 'Hello world'
        }

        stage('step 2') {
            sh 'echo "ni hao"'
        }


    stage('check if PR merged') {
    container('docker-infrastructure-deployment') {
                    dir("emr-ingestor/templates") {
                        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: "graph-${aws_account}", variable: 'credentials']]) {
                            def awsAccount = aws_account
                            def AWS_ACCESS_KEY_ID = env.AWS_ACCESS_KEY_ID
                            def AWS_SECRET_ACCESS_KEY = env.AWS_SECRET_ACCESS_KEY

     sh (script: "aws s3 cp --region us-west-2  s3://profilev2-artifacts/replay_job/gh_2.8.0_linux_amd64.tar.gz ./", returnStdout: true)
     echo 'here'
     sh (script: "tar xvf gh_2.8.0_linux_amd64.tar.gz", returnStdout: true)
     echo 'here2'
     sh (script: "cp gh_2.8.0_linux_amd64/bin/gh /usr/local/bin/", returnStdout: true)
     echo 'here3'
       sh (script: "gh --help",returnStdout: true)
       echo 'here4'
   }
   }
   }
  }
}
