node{
  stage('SCM Checkout'){
    git 'https://github.com/UttaravK/Jenkins_CICD'
  }
  stage('Compile-Package'){
    sh 'mvn package'
  }
  stage('Start-App'){
    sh '
	if pgrep -x gs-serving-web-content-0.1.0.jar > /dev/null
	then 
	   ps | grep gs-serving-web-content-0.1.0.jar | awk {'print $1'} | head -n 1 | xargs kill -6 
        fi
       '
    sh 'java -jar ./target/gs-serving-web-content-0.1.0.jar'
  }
}
