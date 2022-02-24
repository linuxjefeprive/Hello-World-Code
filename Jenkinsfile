pipeline {
    agent any 
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
               stage('Deploy to Site 1') {
            steps {
                echo '> Deploying to Site 1 ...'
                ansiblePlaybook (
                    installation: 'ansible',
                    playbook: '${WORKSPACE}/move-war-to-tomcat.yaml',
                    inventory: '/etc/ansible/hosts'
                )
                echo '> Deployed to Site 1 ...'
            }
               }
    }
}
