node{

stage ('Git Clone'){
git branch : 'main', url: 'https://github.com/wiser15/spring-boot-mongo-docker.git'
}

stage('Maven Build jar'){
def mavenHome = tool name: "MAVEN3.6.1", type: "maven"
  def mavenCMD = "${mavenHome}/bin/mvn"
sh "${mavenCMD} clean package"
}

stage ('Build Docker Image'){
sh "docker build -t wiser15/spring-boot-mongo-docker:latest . <<EOF"
}

stage ('Push Docker Image'){
// withCredentials([string(credentialsId: 'DOCKER_HUB_PASS', variable: 'DOCKER_HUB_PASS' )]) {
// sh "docker login -u wiser15 -p $"{DOCKER_HUB_PASS}"
// }
sh 'docker push wiser15/spring-boot-mongo-docker'
}

}
