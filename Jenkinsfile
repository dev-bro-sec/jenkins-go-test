pipeline {
    agent any
    tools {
        go 'go1.15'
    }
    environment {
        GO114MODULE = 'on'
        CGO_ENABLED = 0 
        GOPATH = "${JENKINS_HOME}/terraform/test/"
    }
    stages {        
        stage('Pre Test') {
            steps {
                echo 'Installing dependencies'
                sh 'go version'
                // sh 'go get -u golang.org/x/lint/golint'
            }
        }
        
        // stage('Build') {
        //     steps {
        //         echo 'Compiling and building'
        //         sh 'go build'
        //     }
        // }

        stage('Test') {
            steps {
                    sh 'curl https://raw.githubusercontent.com/golang/dep/master/install.sh | sh'
                    sh 'cd "${JENKINS_HOME}"/terraform/test/ && go test -v hello_world_app_unit_test.go'             
            }
        }
        
    }
    // post {
    //     always {
    //         // emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
    //         //     recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
    //         //     to: "${params.RECIPIENTS}",
    //         //     subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
    //     }
    // }  
}
