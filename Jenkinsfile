pipeline {

    agent any


    stages {
       stage ('Pull') {
            steps {
               script{
						checkout([$class: 'GitSCM',
     branches: [[name: "*/master" ]],
     userRemoteConfigs: [[credentialsId: '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', url: 'https://github.com/BourguigaSam/CD-PROJECT.git']]
         ])
				    }
            }
        }
		
		/*stage ('Build') {
            steps {
               script{
						sh "ansible-playbook ansible/build.yml -i ansible/inventory/host.yml "
				    }
            }
        }*/
		
		stage ('docker') {
            steps {
               script{
						sh "ansible-playbook ansible/docker.yml -i ansible/inventory/host.yml "
				    }
            }
        }

stage('dockerHub') {
             steps{
                script{
                    sh "ansible-playbook ansible/register.yml -i Ansible/inventory/host.yml"
                }
            }
        }

    }   
}
