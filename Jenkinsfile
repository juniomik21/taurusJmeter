node {
   stage('Build') {
      // Run the Taurus build
   }
   stage('Performance Tests') {
    parallel(
        BlazeMeterTest: {
         bat './Users/megearod/AppData/Local/Taurus/bin/bzt.exe C:/Utils/Rendimiento/PruebasJmx/smoketest.yml'
        },
        Analysis: {
            sleep 60
        })
   }

   stage('Deploy') {
   }
}
