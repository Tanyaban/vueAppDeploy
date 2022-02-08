pipeline {
    stages {
        /* checkout repo */
        stage('Checkout SCM') {
            steps {
                checkout([
                 $class: 'GitSCM',
                 branches: [[name: "master"]],
                 userRemoteConfigs: [[
                    url: 'git@github.ibm.com:Innovation-Lab/hcp-ui.git',
                    credentialsId: 'Tanya Bansal'
                 ]]
                ])
            }
        }
   stage('Build') {
	        /* add tool name as per global tool configuration nodejs name given. This step creates dist folder in jenkins workspace */		
	tools{
	    nodejs 'Nodejs'
	}
			steps {
			    script{
				echo 'Building..'
				sh 'npm install'
			}
			}
		}
		
		stage ('application deploy') {
		
			steps {
                    echo 'started deploying in UCD'
                    step([  $class: 'UCDeployPublisher',
                    siteName: 'UCDHOST',
                    component: [
                    $class: 'com.urbancode.jenkins.plugins.ucdeploy.VersionHelper$VersionBlock',
                    componentName: 'vueComponent',
                    delivery: [
                    $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeliveryHelper$Push',
                    pushVersion: '${BUILD_NUMBER}',
                    baseDir: 'data//workspace//DeployToCloud//vueComponent',
                             ]
                              ],
                    deploy: [
                 $class: 'com.urbancode.jenkins.plugins.ucdeploy.DeployHelper$DeployBlock',
                 deployApp: 'DeployToCloud',
                 deployEnv: "dev",
                 deployProc: 'ApplicationProcess-vueComponent',
                 deployVersions: 'vueComponent:${BUILD_NUMBER}',
                 deployOnlyChanged: false
                         ]
                           ])
                  }
				  }
	}

}


