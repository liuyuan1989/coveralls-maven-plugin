pipeline {
  agent any
  stages {
    stage('Clone Code') {
      steps {
        git(url: 'git@github.com:liuyuan1989/coveralls-maven-plugin.git', branch: 'master')
      }
    }
    stage('Code Analysis') {
      steps {
        sh '''sh "mvn clean"
sh "infer -- mvn compile"'''
      }
    }
    stage('Testing') {
      steps {
        sh '''sh "mvn test"
'''
        junit 'target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        sh 'sh "\'mvn\' -Dmaven.test.skip=true package"'
        archiveArtifacts 'target/*.jar'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo \'pipeline success\''
      }
    }
  }
}