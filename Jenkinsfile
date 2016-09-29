stage('Build') {
    node {
        git url: 'git@github.com:PavelShchetska/boxfuse-sample-java-war-hello.git'
        env.PATH = "${tool 'MAVEN3.3.9'}/bin:${env.PATH}"
        sh 'mvn clean package'
        archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
    }
}

stage('deployToDev') {
    node {
        sh "sleep 6"
    }
}

stage('deployToQA') {
    input 'Do you approve deployment to QA?'
    node {
        sh "sleep 6"
    }
}

stage('deployToStage') {
    input 'Do you approve deployment to Stage?'
    node {
        sh "sleep 6"
    }
}

stage('deployToProd') {
    input 'Do you approve deployment to Prode?'
    node {
        sh "sleep 6"
    }
}