pipeline {
  agent any
  environment {
      MAJOR = '1'
      MINOR = '0'
  }
  stages {
      
    stage('Check Out')  {
        steps {
            git url: 'https://github.com/ppengkkang/uipathpipelinedemo.git', branch: 'main'
        }
    }
    
    stage ('Pack') {
      steps {
        UiPathPack (
          outputPath: "Output\\${env.BUILD_NUMBER}",
          projectJsonPath: "project.json",
          version: [$class: 'ManualVersionEntry', version: "${MAJOR}.${MINOR}.${env.BUILD_NUMBER}"],
          useOrchestrator: true,
          traceLevel: "None",
          orchestratorAddress: "https://cloud.uipath.com/ppengkkang/DefaultTenant",
          orchestratorTenant: "DefaultTenant",
          credentials: [$class: 'UserPassAuthenticationEntry', credentialsId: 'ocadmin']
        )
      }
    }
  }
}

