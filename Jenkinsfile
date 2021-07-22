node {
    stage('Build') {
        sh 'echo "Step One build something else" '
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: https://github.com/cristeyg/DOTT.git]]])
    }
    stage('SonarQube') {
        sh 'echo "Step Two Sonarqube x" '
        sh "ls -a"
        def scannerhome =tool 'sonar';
        withSonarQubeEnv ('sonar'){
            sh """"$(scannerhome)/bin/sonar-scanner \
            -Dsonar.projectKey=Prueba \
            -Dsonar.sources=./cidr_convert_api \
            -Dsonar.host.url=http://ec2-18-188-179-18.us-east-2.compute.amazonaws.com:9000 \
            -Dsonar.login=7650e8fd49440f9aa9b4659ac7d4196024b576b4
        }
    }
    stage('Quality Gate') {
        sh 'echo "Step Three ddd" '
    }
    stage('Testing') {
        sh 'echo "Step Three ddd" '
    }
    stage('Deploy') {
        sh 'echo "Step Three" '
    }
}
