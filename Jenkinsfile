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
            echo "Get the Driver Path ${ChromeDriverPath}"
          }
        }

        stage('Test Log') {
          environment {
            LocalVariable = 'HellowLocal'
          }
          steps {
            writeFile(file: 'LogTestFile.txt', text: "This is the ChromeDriverPath ${ChromeDriverPath} and localvariable Value${LocalVariable}")
          }
        }

      }
    }

    stage('Deploy') {
      parallel {
        when
        {
          branch 'master'
        }

        stage('Deploy') {
          steps {
            input(message: 'Do you want to Deploy ?', id: 'Ok')
            echo 'Deploying the app IIS server'
          }
        }

        stage('Artifacts') {
          steps {
            archiveArtifacts 'LogTestFile.txt '
          }
        }

      }
    }

  }
  environment {
    ChromeDriverPath = 'D:\\Users\\Supriya.Awaghade\\Downloads\\Driver\\chromedriver.exe'
  }
}