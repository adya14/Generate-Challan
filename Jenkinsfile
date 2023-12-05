pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Your build steps here

                // Example: Trigger failure for demonstration
                sh 'exit 1'
            }
        }

        stage('Unit Test') {
            steps {
                // Your unit test steps here

                // Example: Trigger failure for demonstration
                sh 'exit 1'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Your Docker build steps here

                // Example: Trigger failure for demonstration
                sh 'exit 1'
            }
        }

        stage('Deploy') {
            steps {
                // Your deployment steps here
            }
        }
    }

    post {
        failure {
            // Send email on failure
            emailext subject: 'Pipeline Failed: ${currentBuild.fullDisplayName}',
                      body: 'The pipeline has failed. Please check the Jenkins console output for details.',
                      to: 'adya.tiwari20@st.niituniversity.in, somia.kumari20@st.niituniversity.in, tanya.patel20@st.niituniversity.in',
                      recipientProviders: [[$class: 'CulpritsRecipientProvider']]
        }
    }
}
