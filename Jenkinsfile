node {
   stage('Build') {
      // Run the Taurus build
   }
   stage('Performance Tests') {
           bat 'C:/Users/megearod/AppData/Local/Taurus/bin/bzt.exe -o modules.jmeter.path="C:/Utils/Rendimiento/Jmeters/apache-jmeter-5.2.1/bin/jmeter.bat" C:/Utils/Rendimiento/PruebasJmx/smoketest.yml'
   }

   stage('Deploy') {
   }
}
