node {
    stage("checkout"){
		 git url: 'https://github.com/shuvragupta/user-management-service.git',branch: 'master' 
	}
	stage("build"){
		cmd "mvn clean install"
	}
	stage("cloudfoundry_login"){
	    withCredentials([usernamePassword(credentialsId: 'ca1f6060-22d2-4480-8959-f434330dfb47', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            bat 'echo %USERNAME%'
	        bat 'cf login -a https://api.run.pivotal.io -u %USERNAME% -p %PASSWORD%'
	    }
	}
	stage("clodfoundry_push"){
	    bat "cf push"
	}
}