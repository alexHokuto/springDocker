node {
  stage "Checkout"
  checkout scm

  stage "Build"
  
  try {
   // String command = './gradlew clean build'
    String command = 'gradle clean build --stacktrace'
    sh command
  } catch(err) {
    throw err
  }

  stage 'Archive'

 // step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/test/TEST-*.xml'])
  step([$class: 'ArtifactArchiver', artifacts: '**/build/libs/*.jar', fingerprint: true])

  step([$class: 'JacocoPublisher'])
  step([$class: 'FindBugsPublisher', pattern: '**/findbugs/*.xml'])
  step([$class: 'CheckStylePublisher', pattern: '**/checkstyle/*.xml'])
  step([$class: 'PmdPublisher', pattern: '**/pmd/*.xml'])
  step([$class: 'PragprogBuildStep', displayLanguageCode: 'en', indicateBuildResult: true])
  
  
}
