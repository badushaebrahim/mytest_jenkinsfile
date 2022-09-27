pipeline {
    agent any
    environment{
    DOCK=credentials('dockerhub')
}

    stages {
      
            
        
        
        
           stage('init') {
            steps {
                sh "echo $DOCK_PSW"
                echo 'initial'
                sh "node -v"
                sh "docker -v "
                sh "git clone https://github.com/badushaebrahim/dockerd.git"
            }
            
        
        }
        stage("build docker"){
            steps{

                sh "cd dockerd && docker build -t django-pack:1.01.0 . "
            }
        }
        stage("push build "){
            steps{
                sh "docker tag django-pack:1.01.0 badusha/django-pack:1.01.0  "
                sh "echo $DOCK_PSW | docker login -u 'badusha' --password-stdin"
                sh "docker push badusha/django-pack:1.01.0"
            }
        }
        
    }
    // post{
    //     always{
    //         sh'dockerlogout'
    // }
}
