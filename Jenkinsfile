pipeline{

    agent any

    tools{
        maven "maven"
    }

    stages{
        stage("SCM checkout"){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Phanindra-Reddy-Naga/jenkins-ci-cd.git']])
            }
        }
        environment{
            APP_NAME = "spring-docker-cicd"
            RELEASE = "1.0.0"
            DOCKER_USER = "nagakolli"
            IMAGE_NAME = "${DOCKER_USER}"+"/"+"${APP_NAME}"
            IMAGE_TAG = "${RELEASE_NO}-${BUILD_NUMBER}"
        }
        stage("Build process"){
            steps{
                script{
                    bat 'mvn clean install'
                }
            }
        }

       stage("Build Image"){
           steps{
               script{
                   bat 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
               }
           }
       }

       stage("Deploy Image To Hub"){
           steps{
              //withCredentials([usernamePassword(credentialsId: '77b4a400-eca4-4b8f-b70e-7e0cc9b83916', passwordVariable: 'phAnindr@1679', usernameVariable: 'nagakolli')]) {
                bat 'docker login -u nagakolli -p phAnindr@1679'
                //sh 'docker tag spring-cicd:1.0 nagakolli/spring-cicd:1.0'
                bat 'docker push ${IMAGE_NAME}:${IMAGE_TAG}'
                //}
           }

       }



    }

    post{
        always{
            emailext attachLog: true,
            body: '''<html>
            <body>
            <p>Build Status : ${BUILD_STATUS} </p>
            <p>Build Number : ${BUILD_NUMBER} </p>
            <p>Check the <a href="${BUILD_URL}">console output<a/>. </p>
            </body>
            </html>''', mimeType: 'text/html', replyTo: 'phanindrareddy96@gmail.com', subject: 'Pipeline Status : ${BUILD_NUMBER}', to: 'phanindrareddy96@gmail.com'
        }

    }

}