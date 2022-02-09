pipeline {
    agent any
     tools {
    maven 'maven3.8.4'
   }
    stages {

        stage('Unit test') {
            steps {
                  sh 'mvn clean test'
                    }
            }
        stage('build'){
            steps {
                sh 'mvn clean install -DskipTests=true' 
            }
        }
         stage('deploy'){
            steps {
                 sh 'cd /home/osboxes/ansible && ansible-playbook -i hosts deploy.yml' 
            }
        }
        stage('sanity check'){
            steps {
                 sh '/home/osboxes/check.sh'

            }
        }
    }
}
