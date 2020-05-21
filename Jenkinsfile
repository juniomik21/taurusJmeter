node {
	stage('Build'){
		//run the taurus build
	}
	stage('Performance Test'){
		parallel(
			BlazeMeterTest: {
				bat 'bzt smoketest.yml -report'
			}
		)
	}

}
