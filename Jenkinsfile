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
                		sh ssh -A paja@10.251.251.90 "cd ~/jenkins_home/workspace/calculator_JF && docker build -t sh4rkba/calculator ."
				sh ssh -A paja@10.251.251.90 "docker run -d --rm -p 8765:8080 --name calculator sh4rkba/calculator"
				//app = docker.build("sh4rkba/calculator") 
            		}
			steps {
                		sh ssh -A paja@10.251.251.90 "docker run -d --rm -p 8765:8080 --name calculator sh4rkba/calculator"
            		}
        	}
	}
}
