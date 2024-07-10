
pipeline{

    agent any

    environment{
        SONARQUBE_URL = 'http://13.127.141.151:9000'
            
    }
   

    stages{
         
        stage('Git Checkout'){
                   
            steps{
            gitCheckout(
                branch: "dev",
                url: "https://github.com/rajMaurya0502/Java_app_3.0.git"
            )
            }
        }
         
        stage('Static code analysis'){
            steps{
                   
                   withSonarQubeEnv('SonarQube'){
                       sh "mvn -ntp sonar:sona -Dsonar.projectKey=java_app -Dsonar.sources=src -Dsonar.host.url=${SONARQUBE_URL} -Dsonar.login=sqa_0908e617ed2e9f32f7269acafe3e997e41456f16"
               }
            }
       }
       // stage('Quality Gate Status Check : Sonarqube'){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             def SonarQubecredentialsId = 'sonarqube-api'
       //             QualityGateStatus(SonarQubecredentialsId)
       //         }
       //      }
       // }
       //  stage('Maven Build : maven'){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             mvnBuild()
       //         }
       //      }
       //  }
       //  stage('Docker Image Build'){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             dockerBuild("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
       //         }
       //      }
       //  }
       //   stage('Docker Image Scan: trivy '){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             dockerImageScan("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
       //         }
       //      }
       //  }
       //  stage('Docker Image Push : DockerHub '){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             dockerImagePush("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
       //         }
       //      }
       //  }   
       //  stage('Docker Image Cleanup : DockerHub '){
       //   when { expression {  params.action == 'create' } }
       //      steps{
       //         script{
                   
       //             dockerImageCleanup("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
       //         }
       //      }
       //  }      
    }
}
