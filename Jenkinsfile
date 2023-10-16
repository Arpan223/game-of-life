pipeline {
    agent {
        node {
            label 'built-in'
            customWorkspace '/home/ec2-user'
        }
    }
    stages {
        stage ('Checkout') {
            steps {
                sh'''
                sudo git clone https://github.com/Arpan223/game-of-life.git
                '''
            }
        }
        stage ('Build') {
            steps {
                sh '''
                cd /home/ec2-user/game-of-life
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
