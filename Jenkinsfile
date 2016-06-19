node {
    def nodeHome = tool name: 'node-4.4.5', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation'
    env.PATH = "${nodeHome}/bin:${env.PATH}"
    stage 'install npm gulp bower'
    sh "npm install -g npm"
    sh "npm install -g bower gulp-cli"

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
