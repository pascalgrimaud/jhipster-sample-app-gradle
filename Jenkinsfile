node {
    stage 'checkout'
    checkout scm

    stage 'clean'
    sh "./gradlew clean"

    stage 'backend tests'
    sh "./gradlew test"

    stage 'frontend tests'
    sh "gulp test"

    stage 'packaging'
    sh "./gradlew bootRepackage -Pprod -x test"
}
