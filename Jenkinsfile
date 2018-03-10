try {
    timeout(time: 20, unit: 'MINUTES') {
        node('maven') {
            stage('build') {
                openshiftBuild(buildConfig: 'insult-app-wildfly', showBuildLogs: 'true')
            }

            stage('deploy') {
                openshiftDeploy(deploymentConfig: 'insult-app-wildfly')
            }
        }
    }

} catch (err) {
    echo "in catch block"
    echo "Caught: ${err}"
    currentBuild.result = 'FAILURE'
    throw err
}