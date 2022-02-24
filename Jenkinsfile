pipeline {
	agent any
//	agent {
//    docker-slave {
//        label 'jenkins-agent'
        // image 'jenkins-agent-docker'
//    }
// }
//    agent {
//        docker { image 'node:16.13.1-alpine' }
///    }
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
