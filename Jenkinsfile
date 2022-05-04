pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('build docke image'){
            when {
                branch 'master'
                }
            steps{
                script{
                    app=docker.build("nikhilmandy/train-schedule")
                    app.inside{
                        sh 'echo $(curl localhost:8080)'
                    }
                }
            }
        }    
    }
}
