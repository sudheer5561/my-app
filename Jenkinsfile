pipeline{
    agent any

     environment{

        PATH = "/opt/apache-maven-3.6.3/bin:$PATH"

            }

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
