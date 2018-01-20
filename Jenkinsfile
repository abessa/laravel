node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        checkout scm
    }
    
    stage('Build'){
        sh 'composer install --no-script --prefer-dist --no-dev --ignore-platform-reqs'
    }
    
    stage('config') {
        parallel(
            'config cache': {
                echo 'terefa 1'
            },
            'config route': {
                echo 'tarefa 2'
            }
        )
    }
    stage('Docker Build') {
        sh 'docker build -t abessa/laravel:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'docker push abessa/laravel:$BUILD_NUMBER'
    }
}
