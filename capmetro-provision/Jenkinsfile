node {
    stage("Provision") {
        withCredentials([string(credentialsId: 'CAPMETRO_AWS_ACCESS_KEY_ID', variable: 'AWS_ACCESS_KEY_ID'),
                         string(credentialsId: 'CAPMETRO_AWS_SECRET_ACCESS_KEY', variable: 'AWS_SECRET_ACCESS_KEY')]) {

        
            checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                      doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [],
                      userRemoteConfigs: [[url: 'git@github.com:vergeman/capmetro-deploy']]])

            sh 'AWS_ACCESS_KEY_ID=$AWS_ACCESS_KEY_ID AWS_SECRET_ACCESS_KEY=$AWS_SECRET_ACCESS_KEY "$WORKSPACE/ec2_provision.sh"'
        }
    }
}
