pipeline {
    agent any
        stages {
            stage('Build') {
                steps {
                    sh 'echo "Step One build something else" '
                }
            }
            stage('SonarQube') {
                steps {
                    sh 'echo "Step Two Sonarqube x" '
                }
            } 

            stage('Testing') {
                steps {
                    sh 'echo "Step Three ddd" '
                }
            }

            stage('Deploy') {
                steps {
                    sh 'echo "Step Three" '
                    sonar-scanner \
                      -Dsonar.projectKey=Prueba \
                      -Dsonar.host.url=http://ec2-18-222-163-216.us-east-2.compute.amazonaws.com:9000 \
                      -Dsonar.login=7650e8fd49440f9aa9b4659ac7d4196024b576b4
                }
            }
        }
}
