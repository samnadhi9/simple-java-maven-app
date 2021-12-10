pipeline {
    agent { label 'JDK11-MVN3.8.4' }
    triggers { upstream(upstreamProjects: 'starterproject', threshold: hudson.model.Result.SUCCESS) }
    stages {
        stage('scm') {
            steps {
                git 'https://github.com/samnadhi9/simple-java-maven-app'
            }
        }
        stage('build') {
            steps {
                sh '/usr/local/apache-maven-3.8.4/bin/mvn clean package'
            }
        }
    }
}
