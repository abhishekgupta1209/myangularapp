// node {
//     stage('Checkout') {
        
//         deleteDir()
//         checkout scm
//     }

//     stage('NPM Install') {

//         nodejs('NodeJs') {
    // some block
//             bat 'npm install'
//             bat 'ng build --prod'
//             echo "build sccess"
//             bat 'docker login -u "admin" -p "admin" 127.0.0.1:5000'
//             bat 'docker build -t 127.0.0.1:5000/myapp:1.1 .'
            // bat 'docker push 127.0.0.1:8082/repository/images/myapp:latest'
//             bat 'docker push 127.0.0.1:5000/myapp:1.1'
            // bat 'kubectl create secret docker-registry dockersecret --docker-server=127.0.0.1:8082 --docker-username=admin --docker-password=admin'
            // bat 'kubectl apply -f deployment.yaml'

//         }
//         kubeconfig(credentialsId: 'mykubeconfig', serverUrl: 'https://127.0.0.1:50321') {
//     // some block
//         // bat 'kubectl delete deployment angular-deployment'
//         bat 'kubectl apply -f deployment.yaml'
// }
        
//     }
// }
node {
  stage('SCM') {
    checkout scm
  
  def stages=[:]
  stages['SonarQube Analysis'] ={
    def scannerHome = tool 'SonarScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
  stages['build']={
    echo "build sccess"
    echo "ye parallel hai :)"
    stage('sample stage'){
    sh 'echo "hello"'
    }
  }
   parallel(stages)
  }
}
