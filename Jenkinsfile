node {
    stage('Build') {
        sh 'echo "Step One build something else" '
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/cristeyg/DOTT.git']]])
    }
    stage('SonarQube') {
        sh 'echo "Step Two Sonarqube x" '
        sh "ls -a"
        def scannerhome =tool 'sonar';
        withSonarQubeEnv ('sonar'){
            sh """${scannerhome}/bin/sonar-scanner \
            -Dsonar.projectKey=Prueba \
            -Dsonar.sources=./cidr_convert_api \
            -Dsonar.host.url=http://ec2-18-188-51-220.us-east-2.compute.amazonaws.com:9000 \
            -Dsonar.login=025ecbc8c6310700d3880f77779118424b8c3dcd """
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
