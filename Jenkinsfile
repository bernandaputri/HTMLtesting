node{
  def dockerImageName='samanthams/htmltest_$JOB_NAME:$BUILD_NUMBER'
  def dockerContainerName='simplehtml_$BUILD_NUMBER'
  stage('SCM Checkout'){
    git 'https://github.com/SamanthaMeliora/HTMLtest.git'
  }
  
  stage('Build Docker Image'){
    sh "docker build -t ${dockerImageName} ."
  }
  
  stage('Run Docker Image'){
      sh "sudo chmod +x stopscript.sh"
      sh "sudo ./stopscript.sh"
      sh "docker run -p 8082:8080 -d --name ${dockerContainerName} ${dockerImageName}"
      }  
}
