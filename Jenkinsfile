@Library("Shared") _
pipeline{
    agent any
    
    stages{
        stage("Hello"){
    	    steps{
		        script{
			        hello()
		        }       	
    	    }
    	}
        stage("Clone Code"){
            steps{
            	script{
                	clone("https://github.com/piyushadhalikar/node-todo-cicd.git", "master")
                }
            }
        }
        stage("build"){
            steps{
            	script{
                	docker_build("node-app-test","latest","piyusha19")
                }
            }
        }
        stage("test"){
            steps{
                echo "code testing done"
            }
        }
        stage("push to DockerHub"){
            steps{
            	script{
            		docker_push("node-app-test","latest","piyusha19")
            	}    
                echo "code pushed to dockerhub"
            }
        }
        stage("deploy"){
            steps{
            	script{
                	docker_compose()
                }
            }
        }
    }
}
