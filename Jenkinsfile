def gv
pipeline {
	
	agent any
	parameters {
		choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
		booleanParam(name: 'executeTest', defaultValue: 'true',description: '')
	}
	
	stages {
		
		stage("init") {
			
			
			steps {
				script {
					gv = load "script.py"
				}
			
			}
		}
		
		stage("build") {
			
			
			steps {
				script {
					gv.buildApp()
				}
				
			}
		}
		
		stage("test") {
			when {
				expression {
					params.executeTest
				
				}
			}
			
			steps {
				script {
					gv.testApp()
				}
			}
		}
	
		stage("deploy") {
			
			
			steps {
				script {
					gv.deployApp()
				}
			}
		}
	}
}
