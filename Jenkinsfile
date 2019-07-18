pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull ppak4bytes/selenium-docker"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up zalenium search-module"
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