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
                sh 'npm config set registry https://registry.npmjs.org/'
                sh 'npm cache clean --force'
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
                        sh 'docker rm -f ${MY_IMAGE}'
                    }else{
                       echo 'No existing container'git 
                    }
                }
                sh 'docker run -d -p 3000:80 ${MY_IMAGE}'
            }
        }
    }
}
