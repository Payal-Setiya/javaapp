 
node{
   stage('SCM Checkout'){
     git 'https://github.com/Payal-Setiya/javaapp.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
      junit 'target/surefire-reports/**/*.xml'
   }
   
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'Maven', type: 'maven'
        withSonarQubeEnv('SonarQube') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
    }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war root@184.72.94.32:/opt/tomcat/webapps/'
      }
   }
 }
