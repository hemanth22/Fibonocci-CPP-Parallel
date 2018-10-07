node{
try{
    stage('Downloading code'){
    git 'https://github.com/hemanth22/Fibonocci-CPP.git'
    }
    stage('Building'){
              parallel{
                  stage('Building App 1'){
                  sh 'make main'
                  }
                  stage('Building App 2'){
                  sh 'make factorial'
                  }
                  stage('Building App 3'){
                  sh 'make hello'
                  }
              }
         }
    stage('Compile'){
    sh 'make function'
    }
    stage('Execute'){
    sh './Out'
    }
    stage('Clean binary codes'){
    sh 'make clean'
    }
    stage ('Archive'){
    archiveArtifacts '*'
    }
    notify('Success')
    }catch(err){
    notify("Error ${err}")
    currentBuild.result = 'FAILURE'
    }
}

def notify(status){
    emailext (
      to: "root@localhost.localdomain",
      subject: "${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: """<p>${status}: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
        <p>Check console output at <a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a></p>""",
    )
}
