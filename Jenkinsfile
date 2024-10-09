def isDeployCandidate() {
    return true
}

pipeline {
    agent { dockerfile true }

    stages {
        stage('Build APK') {
            when { expression { return isDeployCandidate() } }
            steps {
                echo 'Building APK'
                script {
                    // VARIANT = getBuildType()
                    sh "./gradlew assembleDebug" // -PstorePass=${STORE_PASSWORD} -Pkeystore=${KEYSTORE} -Palias=${KEY_ALIAS} -PkeyPass=${KEY_PASSWORD} bundle${VARIANT}"
                }
            }
        }
    }
}
