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

        stage('Deploy'){
            steps{
                sshagent(['tomcat-ROOT-id']) {
                    sh """
                scp -o StrictHostKeyChecking=no target/myapp.war root@172.31.16.182:/opt/apache-tomcat-9.0.31/webapps/

                /opt/apache-tomcat-9.0.31/bin/shutdown.sh
                /opt/apache-tomcat-9.0.31/bin/startup.sh

                    """      
                                     
                 }

            }
        }
        


    }
}
