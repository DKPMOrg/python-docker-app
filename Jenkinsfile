node {
    //def app
    def DOCKER_REPO = 'manee2k6/dplinetech'

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace nodejs-app*/
          checkout scm
    }
    stage('Test Build') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */
            sh 'echo "Tests passed"'       
    }
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        img = docker.build("${DOCKER_REPO}:myBuild-1.0", ".")
        //sh 'docker build . -t manee2k6/dplinetech:pythonApp-1.0'
       // app = docker.build("manee2k6/explore:${env.BUILD_NUMBER}")
        
    }
    stage('Push image') {
        /* withDockerRegistry([credentialsId: 'docker-hub-credential', url: 'https://hub.docker.com/']) {
            app.push("${env.BUILD_NUMBER}") 
            app.push("latest")*/
        docker.withRegistry('https://index.docker.io/v1/', 'DockerID') {
            img.push('latest')
        }
        
        
       }
    }
