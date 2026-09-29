pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/prathyusha168/jmeter_performance_project_blazedemo.git'
            }
        }

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
