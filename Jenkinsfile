pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Building the .NET Core application'
          }
        }

        stage('Test') {
          steps {
            echo 'Testing the application'
            echo "Get the Driver Path $[ChromeDriverPath]"
          }
        }

      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploying the app IIS server'
      }
    }

  }
  environment {
    ChromeDriverPath = 'D:\\Users\\Supriya.Awaghade\\Downloads\\Driver\\chromedriver.exe'
  }
}