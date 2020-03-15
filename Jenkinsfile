pipeline {
    agent any

    stages {
	
        stage('preparation') {
            steps {
                echo "workspace: ${WORKSPACE}"
                echo "build_tag: ${BUILD_TAG}"
                echo "node_name: ${NODE_NAME}"
                echo "version: ${version}"
            }
        }

        stage('git-eurekaserver') {
            steps {
                echo "get code from git"
                dir(path: "./eurekaserver") {
                    git(
                        branch: "master",
                        credentialsId: "rockOnGithub",
                        url: 'https://github.com/rockrockrockwong/mc.git',
                        changelog: true
                        )
                }
            }
        }


        stage('maven-build') {
            steps {
                echo "maven build"
                sh "mvn -version"
            }
        }

    }



}