node {
	stage('Build'){
		//run the taurus build
	}
	stage('Performance Test'){
		parallel(
			BlazeMeterTest: {
				sh 'bzt smoketest.yml -report'
			}
		)
	}

}
