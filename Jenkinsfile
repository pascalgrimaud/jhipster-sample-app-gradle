node {
    stage 'checkout'
    checkout scm

    stage 'clean package'
    sh "./gradlew clean bootRepackage -Pprod"
}

