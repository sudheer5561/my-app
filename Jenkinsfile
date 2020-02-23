pipeline{
    agent any
        stages{
            stage('SCM GIT Checkout') {
                steps{
                git 'https://github.com/sudheer5561/my-app.git'
                }
            }
            stage('compile and build') {
                steps{
                sh 'mvn clean package'
                sh 'mv target/*.war target/app.war'
                }
            }

            stage('Deploy in development') {

              steps{

            sshagent(['tomcat-ID-deploy'])
              sh 'scp -o StrictHostKeyChecking=no target/app.war ec2-user@172.31.16.182:/opt/apache-tomcat-9.0.31/webapps'

              sh 'ssh ec2-user@172.31.16.182 /opt/apache-tomcat-9.0.31/shutdown.sh'
              sh 'ssh ec2-user@172.31.16.182 /opt/apache-tomcat-9.0.31/startup.sh'



            }

          }


        }
}
