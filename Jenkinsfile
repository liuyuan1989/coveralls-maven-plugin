node {
   stage('Clone Code') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/trautonen/coveralls-maven-plugin.git/'
   }
   stage('Code Analysis') {
       sh "mvn clean"
       sh "infer -- mvn compile"
   }
   stage('Testing') {
       sh "mvn test"
       junit 'target/surefire-reports/TEST-*.xml'
   }
   stage('Package') {
       sh "'mvn' -Dmaven.test.skip=true package"
       archive 'target/*.jar'
   }
   stage('Deploy') {
       echo 'pipeline success'
   }
}
