// STAGE: Intial Pull and Dependency Check
//
// PURPOSE: Will download the github repository upon webhook signal and run a
//          a OWASP Dependency check on the contents.
stage('Intial Pull and Dependency Check') {
  build 'PullCode-DependencyCheck'
}

// STAGE: Static Analysis: Sonarqube Scan
//
// PURPOSE: Runs a static code analysis on the Sonarqube platform on a remote slave worker
//          that already has sonarqube running.
//
// NOTES: As for now, it will pull from the repository after previous job's completion.
//        Ideally, I would want to make sure I download the same version (in case of mass commits)
stage('Static Analysis: Sonarqube Scan') {
  build 'Sonarqube-Scan'
}


stage('Intialize Docker Container for DAST'){
    build 'DAST-Deploy-Initialization'
}

stage('Run ZAP Scan on Containerized Application'){
    build 'DAST-Deploy-ZAP-Scan'
}

stage('Tear Down Docker Container'){
    build 'DAST-Deploy-Tear-Down'
}


//stage('Deploy') {
//  build 'deploy-stage'
//}