node('JDK11-MVN3.8.4') {
    properties([pipelineTriggers([upstream('starterproject, ')])])
    stage('git') {
          git 'https://github.com/samnadhi9/simple-java-maven-app'   
    }
    
    stage('build') {
        sh '''
            echo "PATH=${PATH}"
            echo "M2_HOME=${M2_HOME}"
        '''
        sh '/usr/local/apache-maven-3.8.4/bin/mvn clean package'
    }
    stage('archive') {
        archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
    }
    stage('publish test reports') {
        junit '**/TEST-*.xml'
    }
}