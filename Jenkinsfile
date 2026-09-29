pipeline {
    agent any

    stages {

        stage('Run JMeter') {
            steps {
                bat '''
                cd /d C:\\apache-jmeter-5.6.3\\bin

                del /Q "%WORKSPACE%\\results.jtl"

                rmdir /S /Q "%WORKSPACE%\\report"

                jmeter -n ^
                -t "%WORKSPACE%\\blazetest.jmx" ^
                -l "%WORKSPACE%\\results.jtl" ^
                -e ^
                -o "%WORKSPACE%\\report"
                '''
            }
        }

    }

    post {

        always {

            publishHTML([
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'report',
                reportFiles: 'index.html',
                reportName: 'JMeter Performance Report'
            ])

        }

    }
}