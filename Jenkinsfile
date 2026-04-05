pipeline {
    agent {
        node {
            label 'QA'  
            
        }
    }
           stages{
	      stage('Clone Git Repo'){
                 steps{
			git branch: 'main' , url: 'https://github.com/abhishek-7980/docker-assigement-4.git'
	    }
	}
		stage('Delete old Container'){
		  steps {
			sh 'docker rm -f c1 c2 c3 || true'	
	     }	
	}    
		stage ('Create Docker Volume Q1'){
		  steps {
			sh 'docker volume create container-Q1 '
		}
	}
		stage ('Deploy Q1'){
		  steps {
			sh 'git checkout 2026-Q1'
			sh 'docker run -dp 80:80 -v container-Q1:/usr/local/apache2/htdocs --name c1 httpd'
			sh 'docker cp index.html c1:/usr/local/apache2/htdocs/index.html'
			sh 'docker exec c1 chmod 777 -R /usr/local/apache2/htdocs/index.html'
		}
	}
		stage ('Create Docker Volume Q2') {
		  steps {
			sh 'docker volume create container-Q2'
		}
         }
                 stage ('Deploy Q2'){
		   steps {
			 sh 'git checkout 2026-Q2'
			 sh 'docker run -dp 90:80 -v container-Q2:/usr/local/apache2/htdocs --name c2 httpd'
			 sh 'docker cp index.html c2:/usr/local/apache2/htdocs/index.html'
			 sh 'docker exec c2 chmod 777 -R /usr/local/apache2/htdocs/index.html '
		}
	}
		stage ('Create Docker Volume Q3'){
                  steps {
			sh 'docker volume create container-Q3'
		}
	}
		stage ('Deploy Q3'){
		  steps {
			sh 'git checkout 2026-Q3'
		    sh 'docker run -dp 9080:80 -v container-Q3:/usr/local/apache2/htdocs --name c3 httpd'
			sh 'docker cp index.html c3:/usr/local/apache2/htdocs/index.html'
			sh 'docker exec c3 chmod 777 -R /usr/local/apache2/htdocs/index.html'
		}
	}
}
}
