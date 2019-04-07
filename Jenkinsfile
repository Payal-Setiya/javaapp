  node{
   stage('SCM Checkout'){
     git 'https://github.com/Payal-Setiya/javaapp.git'
   }
   stage('Compile-Package'){
    
      def mvnHome =  tool name: 'Maven', type: 'maven'    
      sh "${mvnHome}/bin/mvn package"
   }
  }
   


