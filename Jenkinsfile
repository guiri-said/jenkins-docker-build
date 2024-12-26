node{
  def app

    stage('Clone') {
        checkout scm
    }

    stage('Build dicker image') {
        app = docker.build("my_nginx")
    }

    stage('Test image') {
        docker.image('my_nginx').withRun('-p 80:80') { c ->
        sh 'sleep 5'  
        sh 'docker ps'
        sh "docker exec ${c.id} curl http://localhost"
	     }
    }
}
