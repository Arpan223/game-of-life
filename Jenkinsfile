pipeline {
    agent {
        node {
            label 'built-in'
            customWorkspace '/opt'
        }
    }
    stages {
        stage ('Checkout') {
            steps {
                sh'''
                rm -rf game-of-life
                sudo git clone https://github.com/wakaleo/game-of-life.git
                '''
            }
        }
        stage ('Build') {
            steps {
                sh '''
                cd /opt/game-of-life
                mvn clean install
                '''
            }
        }
        stage ('Deploy') {
            steps {
                sh 'cp /home/ec2-user/game-of-life/gameoflife-web/target/gameoflife.war /mnt/apache-tomcat-9.0.80/webapps'
            }
        }
    }
}
