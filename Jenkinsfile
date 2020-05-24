pipeline{
	agent {label 'WindowNode'}
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull akbarchandani/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up search-module book-flight-module"
			}
		}
	}
	post{
		always{
			bat "Xcopy /E /I /Y C:\\Users\\akbar\\Documents\\Akbar\\dockeroutput\\output .\\output"
			archiveArtifacts artifacts: 'output/**'
			bat "docker-compose down"			
		}
	}
}