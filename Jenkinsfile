properties([pipelineTriggers([githubPush()])])
node ('linux') {
    git url: 'https://github.com/rossweinstein/java-project.git', branch: 'master'

    stage('Unit Tests') {
        sh 'ant -f test.xml -v'
        junit 'reports/results.xml'
    }
}