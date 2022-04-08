pipeline {
    agent any

    stages {
        stage('拉取') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/github283/springboot.git']]])
            }
        }
        stage('编译') {
            steps {
                sh label: '', script: 'mvn clean package -Dmaven.test.skip=true'
            }
        }
		stage('部署') {
            steps {
                sh '''
                    sh src/main/java/com/test.sh
                '''
            }
        }
    }
}
