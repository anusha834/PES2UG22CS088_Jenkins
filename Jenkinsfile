pipeline { 
    agent any 

    stages { 
        stage('Clone Repository') { 
            steps { 
                checkout([$class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/anusha834/PES2UG22CS088_Jenkins.git']]
                ])
            } 
        }

        stage('Build') { 
            steps { 
                build 'PES2UG22CS088-1'
               
                sh 'g++ -o  main.cp -o output'  // Intentional mistake (should be .cpp)

            } 
        }

        stage('Test') { 
            steps { 
                sh './output'
            } 
        }

        stage('Deploy') { 
            steps { 
                echo 'Deploying...'
            } 
        } 
    }

    post { 
        failure { 
            error 'Pipeline failed'
        } 
    } 
}
