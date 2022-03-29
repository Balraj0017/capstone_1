pipeline{
    agent any
     environment{
        dockerhub_repo = "balraj0017/final"
        dockerhub_creds = 'dockerhub_id'
        dockerImage = ''
     }
    tools { 
        maven 'maven3'
        // Docker 'docker'
    }
    stages
       {
            stage("clean")
            {
                steps{
                    sh "mvn clean"
                }
            }
            stage("Build")
            {
                steps{
                    sh "mvn compile"
                }
                
            }
             stage("TEST")
            {
                steps{
                    sh "mvn test"
                }
            } 
             stage("package")
            {
                steps{
                    sh "mvn package"
                }
            } 
             stage("building docker image"){
                    steps{
                        sh "whoami"
                        script{
                            sudo dockerImage = docker.build dockerhub_repo + ":$GIT_COMMIT-build-$BUILD_NUMBER"
                        }
                       
                     }    
                }
            stage("Pushing the docker image"){
                    steps{
                        script {
                            docker.withRegistry('', dockerhub_creds){
                                dockerImage.push()
                                dockerImage.push('latest')
                                // dockerImage.push('v1')
                            }
                        }
                    }
                }    
        }
}      
