node {
    stage('Build Image') {
        openshiftBuild (
            namespace: 'sock-shop',
            bldCfg: 'carts-build',
            checkForTriggeredDeployments: 'true',
            showBuildLogs: 'true',
            verbose: 'false'
        )
    }

    stage('Verify Build') { openshiftVerifyBuild (
            namespace: 'ci',
            bldCfg: 'carts-build',
            checkForTriggeredDeployments: 'true',
            verbose: 'true'
        )
    }
    stage('Promote Image') {
        openshiftTag (
            srcStream: 'carts',
            srcTag: 'latest',
            destinationStream: 'carts',
            destinationTag: 'latest',
            destinationNamespace: 'sock-shop'
        )
    }
}
