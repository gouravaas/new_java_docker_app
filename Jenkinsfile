pipeline{
	
	agent any
		stages{
			stage ("Pull the code from SCM"){
				steps {
					git 'https://github.com/gouravaas/new_java_docker_app.git'
					}
				}
			stage (" Build the code "){
				steps {
					sh 'mvn clean package'
					}
				}
			stage (" Build the image "){
				agent {
					label "slave1"
					}
				steps {
					sh 'sudo docker build -t java-repo:$BUILD_TAG .'
					sh 'sudo docker tag java-repo:$BUILD_TAG Gouravaas/pipeline-java:$BUILD_TAG'
					}
				}
			}
		
}
