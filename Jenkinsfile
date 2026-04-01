pipeline {
    agent any

    stages {
        stage('Groovy Basics') {
            steps {
                script {
                    // Simple message
                    println "Hello from Jenkins Groovy!"

                    // Loop through a list
                    def fruits = ['Apple', 'Banana', 'Cherry']
                    for (fruit in fruits) {
                        println "I like ${fruit}"
                    }

                    // Run a shell command
                    def dateOutput = sh(script: 'date', returnStdout: true).trim()
                    println "Current date and time: ${dateOutput}"
                }
            }
        }
    }

    post {
        success {
            echo "Groovy script executed successfully!"
        }
    }
}
