
pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}
     
     stages {
           stage('Cloning our Git') {

                 steps {

                       git 'https://github.com/GURU70897/dock_im.git'
                 }
           }

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t gururajp005/nodeapp .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push gururajp005/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}

