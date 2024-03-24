// pipeline{
//
//     agent any
//
//     tools{
//         maven "maven"
//     }
//
//     stages{
//         stage("SCM checkout"){
//             steps{
//                 checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Phanindra-Reddy-Naga/jenkins-ci-cd.git']])
//             }
//         }
//         stage("Build process"){
//             steps{
//                 script{
//                     bat 'mvn clean install'
//                 }
//             }
//         }
// //         stage("Deploy To Container"){
// //             steps{
// //                 deploy adapters: [tomcat9(credentialsId: 'admin-ad', path: '', url: 'http://localhost:9090/')], contextPath: 'jenkinsCiCd', war: '**/*.war'
// //             }
// //         }
// 
//
//
//     }
//
//     post{
//         always{
//             emailext attachLog: true,
//             body: '''<html>
//             <body>
//             <p>Build Status : ${BUILD_STATUS} </p>
//             <p>Build Number : ${BUILD_NUMBER} </p>
//             <p>Check the <a href="${BUILD_URL}">console output<a/>. </p>
//             </body>
//             </html>''', mimeType: 'text/html', replyTo: 'phanindrareddy96@gmail.com', subject: 'Pipeline Status : ${BUILD_NUMBER}', to: 'phanindrareddy96@gmail.com'
//         }
//
//     }
//
// }
//
// //SCM checkout
// //build
// //deploy the war
// //Email trigger