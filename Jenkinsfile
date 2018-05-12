properties([pipelineTriggers([githubPush()])])
node ('linux') {
    git url: 'https://github.com/rossweinstein/java-project.git', branch: 'master'

    stage('Unit Tests') {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }

    stage('Build') {
        sh 'ant -f build.xml -v'
    } 

    stage('Deploy') {
        sh 'aws s3 cp ${WORKSPACE}/dist/rectangle-${env.Build_ID}.jar s3://rw-assignment10/rectange-${env.Build_ID}.jar'
    }
}