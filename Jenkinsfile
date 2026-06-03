pipeline {  
    agent any  
        stages {  
       	    stage("git_checkout") {  
           	    steps {  
              	    echo "cloning repository" 
              	    echo "repo cloned successfully"  
              	    }  
         	    } 
        }
pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Akshu1520/onlinebookstore.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t onlinebookstore .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop onlinebookstore || true
                docker rm onlinebookstore || true

                docker run -d \
                --name onlinebookstore \
                -p 8081:80 \
                onlinebookstore
                '''
            }
        }
    }
}}
