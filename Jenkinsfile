pipeline {
	agent any
	stages {
		stage("Compile") {
			steps {
				sh "./gradlew compileJava"
			}
		}
		stage("Unit test") {
			steps {
				sh "./gradlew test"
			}
		}
		stage("Package") {
			steps {
				sh "./gradlew build"
			}
		}
		 stage('Initialize Docker') {
        		def dockerHome = tool 'MyDocker'
        		env.PATH = "${dockerHome}/bin:${env.PATH}"
    		}
		stage("Docker build") {
			steps {
				sh "docker build -t sh4rkba/calculator ."
			}
		}
	}
}
