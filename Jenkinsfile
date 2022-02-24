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
                		sh 'ssh -A cluster@10.251.251.90 "cd ~/jenkins_home/workspace/calculator_JF && docker build -t sh4rkba/calculator ."'
            		}
		}
		stage("Docker run") {
			steps {
				//sh 'ssh -A paja@10.251.251.90 "docker stop calculator"'
				sh 'ssh -A cluster@10.251.251.90 "docker stop calculator||true && docker run -d --rm -p 8765:8080 --name calculator sh4rkba/calculator"'
            		}
        	}
	}
}
