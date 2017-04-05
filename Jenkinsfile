stage('Build') {
    node {
        git url: 'https://github.com/PavelShchetska/boxfuse-sample-java-war-hello.git'
        env.PATH = "${tool 'MAVEN3.3.9'}/bin:${env.PATH}"
        sh 'mvn clean package'
        archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
    }
}

/*stage('SonarQube analysis') {
    node {
        withSonarQubeEnv('sonar') {
            env.PATH = "${tool 'MAVEN3.3.9'}/bin:${env.PATH}"
            sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.2:sonar'
        }
    }
}*/

stage('deployToDev') {
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://192.168.56.2:81/manager/text/deploy?path=/hello-1.0&update=true"'
        //sh 'sleep 20'
    }
}

stage('deployToQA') {
    input 'Do you approve deployment to QA?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://192.168.56.2:82/manager/text/deploy?path=/hello-1.0&update=true"'
        //sh 'sleep 20'
    }
}

stage('deployToStage') {
    input 'Do you approve deployment to Stage?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://192.168.56.2:83/manager/text/deploy?path=/hello-1.0&update=true"'
        //sh 'sleep 20'
    }
}

stage('deployToProd') {
    input 'Do you approve deployment to Prode?'
    node {
        sh 'curl -v -u admin:tomcat -T "./target/hello-1.0.war" "http://192.168.56.2:84/manager/text/deploy?path=/hello-1.0&update=true"'
        //sh 'sleep 20'
    }
}
