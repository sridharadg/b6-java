pipeline
{
    agent any
    tools
    {
        maven 'm1'
    }       
    stages 
    {
         stage('clone') 
         {
             steps 
             {
checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git@github.com:sridharadg/b6-java.git', url: 'https://github.com/sridharadg/b6-java.git']])            }
         }

         stage('build') {
             steps {
                sh 'mvn clean install'
             }   
            }

        stage('test') {
             steps {
                  sh 'mvn test'
            }

    post {
      always {
            archiveArtifacts artifacts: 'target/**.jar', followSymlinks: false
            junit 'target/surefire-reports/*.*xml'
          
      }
    }
  }

  
}

}
