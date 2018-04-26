properties([pipelineTriggers([githubPush()])])
node ('linux') {
    git url: 'https://github.com/rossweinstein/java-project.git', branch: 'master'
    stage('UnitTests') {
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
}
