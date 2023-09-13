pipeline {
    agent any
    tools{
        nodejs 'npm'
    }
    environment{
        MY_IMAGE='react-image'
    }
    stages {
        stage('Build') {
            steps {
                script{
                    def existImageID= sh(script: 'docker ps -aq --name=\${MY_IMAGE}',returnStdout:true)
                    echo 'ExistImageID:${existImage}'
                    if(existImage){
                        echo '${extistImage} is removing ...'
                        sh 'docker rmi -f ${MY_IMAGE}'
                    }else{
                        sh 'docker build -t \${MY_IMAGE} .'
                    }
                }
            }
        }
        stage('Test') {
            steps {
                echo "Testing .... dg mix teh"
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 3000:80 ${MY_IMAGE}'
            }
        }
    }
}