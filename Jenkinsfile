node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'http://192.168.1.200:9091/loperf/myjsf.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'Maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
          // sh 'mvn -f otherdirectory/pom.xml clean install'
         sh "'${mvnHome}/bin/mvn' -f jsf_jdbcPipeline/pom.xml clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Test') {
      //junit '**/target/surefire-reports/TEST-*.xml'
     //archive 'target/*.war'
     echo 'Test'
   }
      stage('Deploy on server') {
      //junit '**/target/surefire-reports/TEST-*.xml'
     //archive 'target/*.war'
    // sh "scp '/var/lib/jenkins/workspace/pipeline_build_etc/test_srv/target/test_srv.war' root@192.168.1.203:/opt/tomcat/webapps"
   //sh 'ssh root@192.168.1.203 ls /'
    echo 'Deploy'
          
      }
}