def remote = [:]
remote.name = 'dembele'
remote.host = '3.236.174.133'
remote.port = 22
remote.allowAnyHosts = true


pipeline {
    agent any


    stages {
        stage('gitclone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'main', credentialsId: '7b67be65-92ac-4c3b-9c28-fbbf15a10647' , url: 'https://github.com/subhadipdasgit/apache.git'
            }
        }        
        
       stage('Deployment'){
         steps {
            script {
            withCredentials([usernamePassword(credentialsId: 'bubunid', passwordVariable: 'pass', usernameVariable: 'user')]) {
            remote.user = user
            remote.password = pass
            sshPut remote: remote, from: "index.html", into: "/var/www/html"
            }
           }
         }
      }
   }
}
