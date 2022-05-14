pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        
        stage('Sonar-Report') {
            steps {
                bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.analysis.mode=publish org.codehaus.sonar-plugins.pdf-report:maven-pdfreport-plugin:1.3:generate'
            }
        }

        stage('Deploy') {
            steps {
                bat 'mvn clean deploy'
            }
        }
    }
}
