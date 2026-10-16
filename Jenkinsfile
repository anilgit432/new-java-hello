pipeline {
    agent any                       // run on any available Jenkins node

    tools {                         // names must match Manage Jenkins > Tools
        maven 'my maven'           // 
        jdk   'Java_home'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/anilgit432/new-java-hello.git'
            }
        }

        stage('Build & Package') {
            steps {
                sh 'mvn clean package'          // creates target/*.war , also note Sh is fr linux and bat is for Windows
				sh 'ls -l target\\*.war'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                // Simple copy: Jenkins and Tomcat on the SAME machine.
                // Tomcat auto-deploys any WAR dropped into webapps/.
                sh 'cp target/*.war /opt/homebrew/Cellar/tomcat@9/9.0.122/libexec/webapps/'
            }
        }
    }
}
