pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	git 'https://github.com/DivyaBathini/staragilekart.git'
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
		sh 'sshpass -p "divya123" scp /gamut/target/gamutkart.war divya@172.31.37.51:/home/divya/apache-tomcat-9.0.86/webapps/'
	}
    }
}
}
