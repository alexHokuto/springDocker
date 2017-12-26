node {
  stage "Checkout"
  checkout scm

  stage "Build"
  
  try {
    String command = './gradlew clean build publish'
    sh command
  } catch(err) {
    throw err
  }

  stage 'Archive'
  step([$class: 'ArtifactArchiver', artifacts: '**/build/libs/*.jar', fingerprint: true])
  
}
