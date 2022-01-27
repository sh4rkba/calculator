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
        	stage("Docker build") {
            		steps {
                		sh "docker build -t sh4rkba/calculator ."
				//app = docker.build("sh4rkba/calculator") 
            		}
        	}
	}
}
