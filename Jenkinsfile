node {
    stage('Check SCM') {
        sh 'echo "Step One build something else" '
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/cristeyg/DOTT.git']]])
    }
    stage('SonarQube') {
        sh 'echo "Step Two Sonarqube x" '
        def scannerhome =tool 'sonar';
        withSonarQubeEnv ('sonar'){
            sh """${scannerhome}/bin/sonar-scanner \
            -Dsonar.projectKey=Prueba \
            -Dsonar.sources=./cidr_convert_api \
            -Dsonar.host.url=http://ec2-3-137-171-147.us-east-2.compute.amazonaws.com:9000 """
        }
    }
    stage('Build') {
        sh 'sudo docker build -t cristeyg/ruby .'
    }
    stage('Testing') {
        sh 'echo "Step Three ddd" '
    }
    stage('Deploy') {
        sh 'sudo docker run -d --name ruby -p 80:8081 cristeyg/ruby '
    }
}
