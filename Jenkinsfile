pipeline{
      agent any
      stages {
          stage('Downloading code') {
          steps{
          git 'https://github.com/hemanth22/Fibonocci-CPP-Parallel.git'
          }
          }// Downloading
          stage('Building') {
          parallel {
                   stage('Building App 1') {
                          steps {
                          sh 'make main' 
                          }
                  }// Building app1
                  stage('Building App 2') {
                      steps {
                      sh 'make factorial'
                      }
                  }// Building app2
                  stage('Building App 3') {
                      steps{
                      sh 'make hello'
                      }
                  }// Building app3
          } // parallel
          } // Building
          stage('Compile') {
          steps {
          sh 'make function'
          }
          } //Compile
          stage('Execute') {
          steps {
          sh './Out'
          }
          } // Execute
          stage('Clean binary codes') {
          steps {
          sh 'make clean'
          }
          } // Clean
          stage ('Archive') {
          steps {
          archiveArtifacts '*'
          }
          } // Archive
      } // stages
} //pipeline
