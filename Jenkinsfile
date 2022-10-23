pipeline {
    agent any
    parameters { 
	   choice(name: 'BRANCH_TO_BUILD', choices: ['master', 'ut', 'uat'], description: '') 
	   string(name: 'MVN_GOAL', defaultValue: 'mvn package', description: 'Who should I say hello to?')
	   }
    stages {
        stage('Hello') {
            steps {
                git branch: "${params.BRANCH_TO_BUILD}", url: 'https://github.com/awspandian10/sping-pet-clinic.git'
            }
        }
      stage('Build'){
          steps {
		    bat "${params.MVN_GOAL}"
		}
		}
      stage('Archive Results'){
          steps {
		    junit '**/surefire-reports/*.xml'
		}
		}		
    }
}
