pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                sh "mvn --version"
                
            }
            
        }
        stage("Build"){
            steps{
                sh "mvn package"
                
            }
            
        }
        stage("A Deploy on Alma"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcatservercred', path: '', url: 'http://192.168.230.3:8080')], contextPath: '/app', war: '**/*.war'
                //deploy on container -> plugin
                
            }
            
        }
        
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
