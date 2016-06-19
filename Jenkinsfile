node {
    def nodeHome = tool name: 'node-4.4.5', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    env.PATH = "${nodeHome}/bin:${env.PATH}"

    stage 'check environment'
    sh "node -v"
    sh "npm -v"
    sh "bower -v"
    sh "gulp -v"

    stage 'checkout'
    checkout scm

    stage 'link gulp locally'
    sh "npm link gulp"

    stage 'clean'
    sh "./gradlew clean"

    stage 'backend tests'
    sh "./gradlew test"

    stage 'frontend tests'
    sh "gulp test"

    stage 'packaging'
    sh "./gradlew bootRepackage -Pprod -x test"
}
