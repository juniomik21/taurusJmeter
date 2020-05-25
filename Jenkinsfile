node {
	stage('Build'){
		//run the taurus build
	}
	stage('Performance Test'){
	 parallel(
	  BlazeMeterTest: {
		dir('C:\Users\megearod\.bzt'){
		 bat 'bzt smoketest.yml -report'
		}
	)
	},
	Analysis: {
	sleep 60	
	})
 }
	stage('Deploy'){
	}
}
