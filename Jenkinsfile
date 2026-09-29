pipeline {
    agent any

    stages {

        stage('Run JMeter') {
            steps {
                bat '''
                cd /d C:\\apache-jmeter-5.6.3\\bin

                del /Q C:\\projectsforperformance\\results.jtl

                rmdir /S /Q C:\\projectsforperformance\\report

                jmeter -n ^
                -t "%WORKSPACE%\\blazetest.jmx" ^
                -l C:\\projectsforperformance\\results.jtl ^
                -e ^
                -o C:\\projectsforperformance\\report
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
                reportDir: 'C:/projectsforperformance/report',
                reportFiles: 'index.html',
                reportName: 'JMeter Performance Report'
            ])
        }
    }
}