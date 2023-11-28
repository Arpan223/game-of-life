pipeline {
    agent {
        node {
            label 'built-in'
            customWorkspace '/opt/project'
        }
    }
    stages {
        stage ('Checkout') {
            steps {
                sh'''
                sudo git clone https://github.com/wakaleo/game-of-life.git
                '''
            }
        }
        stage ('Build') {
            steps {
                sh '''
                cd /opt
                mvn clean install
                '''
            }
        }
        stage ('Deploy') {
            steps {
                sh 'cp /opt/gameoflife-web/target/gameoflife.war /mnt/apache-tomcat-9.0.83/webapps'
            }
        }
    }
}
