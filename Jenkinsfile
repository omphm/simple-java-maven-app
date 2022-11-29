pipeline{
    agent{
        docker {
            image 'maven:3.8.1-adoptopenjdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    options {
            skipStagesAfterUnstable()
    }
    stages{
        stage("A"){
            steps{
                echo "======== executing A == Anurag-changes again ======"
                sh 'mvn -B -DskipTests clean package'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                echo "======++++running Test++++===="
                sh 'mvn test'
            }
        }
    }
    post{
        always{
            echo "========always========"
            junit "target/surefire-reports/*.xml" 
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}