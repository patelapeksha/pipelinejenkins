node{
   stage('SCM Checkout'){
     git 'https://github.com/javahometech/my-app'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }
   stage('Deploy to Tomcat'){
      
      sshagent(['tomcat-dev']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@54.172.133.39:/home/ec2-user/apps/tomcat/apache-tomcat-9.0.21/webapps/'
      }
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Apeksha''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'apyepatel95@gmail.com'
   }
   
