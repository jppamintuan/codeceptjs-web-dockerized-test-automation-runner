pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull jppamintuan/codeceptjs-web-dockerized-test:latest"
			}
		}
		stage("Start Grid & Run Test"){
			steps{
				sh "docker-compose -f docker-compose.yaml up --exit-code-from codeceptjs-web-dockerized-test --no-color"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: '/source/reports/**'
			sh "docker-compose down"
		}
	}
}