pipeline {
    agent any
	
	triggers {
        cron('H */4 * * 1-5')
    }
	
	tools {
        //工具名称必须在Jenkins 管理Jenkins → 全局工具配置中预配置。
        maven 'maven3'
		jdk 'jdk8'
		docker 'docker'
    } 

    stages {
	
        stage('preparation') {
            steps {
                echo "workspace: ${WORKSPACE}"
                echo "build_tag: ${BUILD_TAG}"
                echo "node_name: ${NODE_NAME}"
            }
        }

        stage('git-eurekaserver') {
            steps {
                echo "get code from git"
                dir(path: "./") {
                    //git(
                    //    branch: "master",
                    //    credentialsId: "rockOnGithub",
                    //    url: 'https://github.com/rockrockrockwong/mc.git',
                    //    changelog: true
                    //    )
					//以上可以使用如下定义，不需要另外写git命令
					checkout scm
                }
            }
        }


        //stage('maven-build') {
        //    steps {
        //        echo "maven build"
        //        bat "mvn -version"
		//		dir(path: "./eurekaserver") {
		//		    bat "dir" 
		//		    bat "mvn clean"
		//		    bat "mvn package"
		//		}
        //    }
        //}
		
		stage('docker-build') {
		    steps {
				echo "docker build"
				bat "docker --version"
			}
		}

    }



}