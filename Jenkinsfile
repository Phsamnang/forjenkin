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
                sh 'npm config set fetch-retry-mintimeout 20000 | npm config set fetch-retry-maxtimeout 120000'
                 sh 'docker build -t \${MY_IMAGE} .'
            }
        }
        stage('Test') {
            steps {
                echo "Testing .... dg mix teh"
            }
        }
        stage('Deploy') {
            steps {
                script{
                def existImageID= sh(script: 'docker ps -aq -f name="${MY_IMAGE}"',returnStdout:true)
                    echo 'ExistImageID:${existImage}'
                    if(existImage){
                        echo '${extistImage} is removing ...'
                        sh 'docker rmi -f ${MY_IMAGE}'
                    }else{
                       
                    }
                }
                sh 'docker run -d -p 3000:80 ${MY_IMAGE}'
            }
        }
    }
}
