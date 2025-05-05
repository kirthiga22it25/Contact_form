pipeline {
  agent any

  stages {
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Start Server') {
      steps {
        script {
          sh 'nohup npm start &'
          sleep 3
        }
      }
    }

    stage('Test API') {
      steps {
        sh '''
          curl -X POST http://localhost:3000/api/contact \
          -H "Content-Type: application/json" \
          -d '{"name":"Jenkins","email":"jenkins@ci.com","message":"Hello"}'
        '''
      }
    }
  }
}
