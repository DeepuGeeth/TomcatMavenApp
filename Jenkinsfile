pipeline {  
    agent any  
    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git url: 'https://github.com/DeepuGeeth/TomcatMavenApp.git'
                    echo "Checkout successful";
                } 
            }
            stage ('Compile') {  
                  steps{
                    sh 'mvn compile'
                    echo "test successful";
                    
                } 
            }
            stage ('Build') {  
                  steps{
                    sh 'mvn -B clean package'
                    echo "build successful";
                    
                } 
            }
             stage ('Test') {  
                  steps{
                    sh 'mvn test'
                    echo "test successful";
                } 
            }
            
            stage ('Deploy') {
                 steps{
                 deploy adapters: [tomcat9(path: '', url: 'http://52.66.161.110:8080/')], contextPath: 'TomcatMavenApp', onFailure: false, war: '**/*.war'
                 echo "Deploy successful";
            }
        }
            stage ('Monitor') { 
                 steps{ 
                 echo "Now you can monitor!";
           }
        }
    }
}
