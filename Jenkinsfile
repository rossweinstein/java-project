properties([pipelineTriggers([githubPush()])])
node ('linux') {
    git url: 'https://github.com/rossweinstein/java-project.git', branch: 'master'
    stage('UnitTests') {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    stage('Build') {
        sh 'ant -f build.xml -v'
    }

    stage('Deploy') {
        sh 'aws s3 cp /workspace/dist/rectangle-'+${env.BUILD_ID}+'.jar s3://rw-assignment10/rectangle-'+${env.BUILD_ID}+'.jar'
    }
}
