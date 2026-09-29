pipeline {
    agent any

    stages {

        stage('Run JMeter') {
            steps {
                bat '''
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
}