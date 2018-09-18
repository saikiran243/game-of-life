node('linux'){
    stage('SCM') {
        git 'https://github.com/saikiran243/game-of-life.git'
    } 
    stage('Build & Package') {
        sh 'mvn clean package
    }
    stage('Build Docker Image') {
	    sh 'docker build -t saikiran243/gol:1 gameoflife-web/Dockerfile'
	}
    stage('Run Docker image') {
	    sh 'docker run -d -p 8080:8080 --name app saikiran243/gol:1'
    }   
    stage('Results'){
        archive 'gameoflife-web/target/gameoflife.war'
        junit 'gameoflife-web/target/surefire-reports/*.xml'
    }
}    
