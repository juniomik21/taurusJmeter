node {
   stage('Build') {
      // Run the Taurus build
   }
   stage('Performance Tests') {
    parallel(
        BlazeMeterTest: {
            dir ('C:\Users\megearod\.bzt') {
               bat 'bzt smoketest.yml -report'
            }
        },
        Analysis: {
            sleep 60
        })
   }

   stage('Deploy') {
   }
}
