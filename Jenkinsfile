node{
  def app

    stage('Clone') {
	sh 'echo "BEFORE CHECKOUT"'
	sh 'pwd'
	sh 'ls'    
        checkout scm
	sh 'echo "AFTER CHECKOUT"'
	sh 'pwd'
	sh 'ls'
    }

    stage('Build dicker image') {
        app = docker.build("my_nginx")
    }

    stage('Test image') {
        docker.image('my_nginx').withRun('-p 80:80') { c ->
        sh 'sleep 20'  
        sh 'docker ps'
        sh "docker exec ${c.id} curl http://localhost"
	     }
    }
}
