pipeline {
  agent {
      label 'maven'
  }
  stages {
    stage('Build WAR') {
      steps {
        git url: 'https://github.com/benemon/jws-fuse-example'
        sh "cp .settings.xml ~/.m2/settings.xml"
        sh "mvn package -DskipTests=true -Dbuild.finalName=ROOT"
      }
    }
    stage('Build Image') {
      steps {
        script {
          openshift.withCluster() {
            openshift.withProject() {
              openshift.startBuild("hello-jws",
                                   "--from-file=target/ROOT.war",
                                   "--wait")
            }
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        script {
          openshift.withCluster() {
            openshift.withProject() {
              def result, dc = openshift.selector("dc", "hello-jws")
              dc.rollout().latest()
              timeout(10) {
                  result = dc.rollout().status("-w")
              }
              if (result.status != 0) {
                  error(result.err)
              }
            }
          }
        }
      }
    }
  }
}i
