pipeline {
    agent any
    stages {
        stage('STAGE TEST') {
            steps {
                script{
                   env.STAGE='STAGE TEST'
                   env.channel='C04BPL2A5E3'
                   
                   sh 'echo "Testins stage && Slack"'
                   sh 'ssh root@192.168.1.1' 
                }
            }
			post{
				success{
					slackSend color: 'good', channel: "${env.channel}", message: "[Fabian Castillo] ${JOB_NAME} Ejecucion Exitosa.", teamDomain: 'D044QHDN0NB', tokenCredentialId: 'token-slack'
				}
				failure{
					slackSend color: 'danger',channel: "${env.channel}", message: "[Fabian Castillo] ${JOB_NAME} Ejecucion fallida en stage [${env.STAGE}]", teamDomain: 'D044QHDN0NB', tokenCredentialId: 'token-slack'
				}
			}
        }
    }
}