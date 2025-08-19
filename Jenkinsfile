Pipeline{
    agent any

        stages{
            stage ('scm_checkout'){
                steps{
                git 'https://github.com/Anik-git96/webapp-java.git'
                }
            }
            
            stage ('build package'){
                steps{
                    sh 'mvn clean package'
                }
            }

            stage ('deploy to tomcat'){
                steps{
                    sshagent(['tomcat']) {
                        sh 'scp -o target/webapp.war ec2-user@65.0.178.25:/usr/share/tomcat/webapps'
                    }
                }
            }
        }
    }