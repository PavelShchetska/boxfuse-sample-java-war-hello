stage('Build') {
    node {
        git url: 'https://github.com/PavelShchetska/boxfuse-sample-java-war-hello.git'
        env.PATH = "${tool 'MAVEN3.3.9'}/bin:${env.PATH}"
        sh 'mvn clean package'
        archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
    }
}

stage('deployToDev') {
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://172.17.0.3:8080/manager/text/deploy?path=/hello-1.0&update=true"'
    }
}

stage('deployToQA') {
    input 'Do you approve deployment to QA?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://172.17.0.4:8080/manager/text/deploy?path=/hello-1.0&update=true"'
    }
}

stage('deployToStage') {
    input 'Do you approve deployment to Stage?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://172.17.0.5:8080/manager/text/deploy?path=/hello-1.0&update=true"'
    }
}

stage('deployToProd') {
    input 'Do you approve deployment to Prode?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://172.17.0.6:8080/manager/text/deploy?path=/hello-1.0&update=true"'
    }
}
