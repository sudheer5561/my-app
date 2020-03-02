pipeline{
    agent any

    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/sudheer5561/my-app.git'
            }
            
        }

        stage('Build'){
            steps{
                sh 'mvn clean package'
                sh 'mv target/*.war target/myapp.war'
            }
        }
        


    }
}
