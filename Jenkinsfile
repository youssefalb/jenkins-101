pipeline {
  agent none  // No global agent. Each matrix combination will use its own.
  
  stages {
    stage('Matrix Example') {
      matrix {
        axes {
          axis {
            name 'OS'
            values 'linux', 'windows'
          }
          axis {
            name 'JDK'
            values '8', '11'
          }
        }

        // Agent section inside matrix — assigns the job to a node with this label.
        agent { label "${OS}" }

        stages {
          stage('Build & Test') {
            steps {
              echo "Test Running on ${OS} with JDK ${JDK}"
              sh 'mvn test'
            }
          }
        }

        // // Optional filtering logic (controls which combinations are allowed)
        // when {
        //   expression { 
        //     (OS == 'linux' && JDK == '11') || (OS == 'windows' && JDK == '8') 
        //   }
        // }
      }
    }
  }
}
