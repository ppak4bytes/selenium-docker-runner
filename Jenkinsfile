pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull ppak4bytes/selenium-docker"
			}
		}
		stage("Start grid"){
			steps{
				sh "docker-compose up -d zalenium --no-color"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up search-module --no-color"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			sh "sudo rm -rf output/"
		}
	}
}