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
            -Dsonar.sources=./cidr_convert_api """
        }
    }
    stage('Build') {
        sh 'docker build -t cristeyg/app .'
    }
    stage('Testing') {
        sh 'tests.rb'
    }
    stage('Deploy') {
        sh 'docker run -d --name ruby -p 80:8081 cristeyg/app '
    }
}
