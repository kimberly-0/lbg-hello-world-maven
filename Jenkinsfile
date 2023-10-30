pipeline {
        agent any

        tools {
            // Install the Maven version configured as "M3" and add it to the path.
            maven "M3"
        }

        stages {
            stage('Checkout') {
                steps {
                    // Get some code from a GitHub repository
                    git branch: 'main', url: 'https://github.com/kimberly-0/lbg-hello-world-maven'
                }
            }
            stage('Compile') {
                steps {
                    // Run Maven on a Unix agent.
                    sh "mvn clean compile"
                }
            }
            stage('Test') {
                steps {
                    sh "mvn test"
                }
            }
            stage('Package') {
                steps {
                    // Skip tests and compiling for the Package stage
		    sh "mvn -Dmaven.test.skip -Dmaven.compile.skip package"
                }
            }
        }
}
