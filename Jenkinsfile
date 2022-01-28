pipeline {
	//agent docker
	agent {
    docker {
        label 'docker'
        image 'jenkins/agent'
    }
}

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
			}
		}
	}
}
