pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	                git url: 'https://www.github.com/DivyaBathini/staragilekart.git,branch:'main'
	    	}
        }
	 stage ('Build'){
	        steps {
			sh 'mvn clean install'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'sshpass -p "divya123" scp /target/gamutkart.war divya@172.31.37.51:/home/divya/apache-tomcat-9.0.86/webapps/'
	}
    }
}
}
