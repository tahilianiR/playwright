# Running in Jenkins

A minimal declarative pipeline:

```groovy
pipeline {
  agent any
  stages {
    stage('Install') {
      steps {
        sh 'npm ci'
        sh 'npx playwright install --with-deps'
      }
    }
    stage('Test') {
      steps {
        sh 'npx playwright test'
      }
    }
  }
  post {
    always {
      publishHTML(target: [
        reportDir: 'playwright-report',
        reportFiles: 'index.html',
        reportName: 'Playwright Report'
      ])
    }
  }
}
```

`publishHTML` needs the HTML Publisher plugin. Set `CI=true` in the environment so config values like `retries` switch to CI mode.

## My notes

- 
