pipeline{
    agent any

    environment{
        NODE_VERSIONS = '18.x'
    }

    tools{
        nodejs "${NODE_VERSIONS}"
    }

    stages{
        stage("Checkout"){
            steps{
                git branch: "master", url: "https://github.com/Radomaster99/RegistryApp"
            } 
        }

        stage("install dependencies"){
            steps{
                script{
                        bat 'npm install'
                    }
                }
            }
        }
        stage("Starting application, then run tests"){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on https://localhost:8090'
                    bat 'npm test'
                }
            }
        }
        post{
            always{
                echo "CI pipeline complited"
            }
        }
    }
}