pipeline {
	agent any

//	options {
//		buildDiscarder(logRotator(numToKeepStr: '10'))
//	}

	parameters {
		booleanParam name: 'RUN_TESTS', defaultValue: true, description: 'Run Tests?'
		booleanParam name: 'RUN_ANALYSIS', defaultValue: false, description: 'Run Static Code Analysis?'
		booleanParam name: 'DEPLOY', defaultValue: flase, description: 'Deploy Artifacts?'
	}

	stages {
        stage('Build') {
            steps {
					sh 'npm install'
            }
        }

        stage('Test') {
            when {
                environment name: 'RUN_TESTS', value: 'true'
            }
            steps {
                sh 'npm test'
            }
        }

//        stage('Analyse') {
//            when {
//                environment name: 'RUN_ANALYSIS', value: 'true'
//            }
//            steps {
//                sh label: '', returnStatus: true, script: 'cppcheck . --xml --language=c++ --suppressions-list=suppressions.txt 2> cppcheck-result.xml'
//                publishCppcheck allowNoReport: true, ignoreBlankFiles: true, pattern: '**/cppcheck-result.xml'
//            }
//        }

//        stage('Deploy') {
//            when {
//                environment name: 'DEPLOY', value: 'true'
//            }
//            steps {
//                sh label: '', returnStatus: true, script: '''cp jenkinsexample ~
//                cp test/testPro ~'''
//            }
//        }
	}
}
