pipeline {
    agent {
        label 'stm32'
    } 

    environment {
        EXAMPLE_DIR = 'examples/STM32F103C8T6'
        BUILD_TYPE  = 'Debug'
        TARGET_MCU  = 'STM32F103C8Tx'
    }

    stages {
        stage('Checkout') {
            steps {
                echo '========================================='
                echo 'Checking out code'
                echo '========================================='
                checkout scm
            }
        }

        stage('Configure') {
            steps {
                echo '========================================='
                echo 'Configure'
                echo '========================================='
                sh '''
                    cmake -B ${WORKSPACE}/build/stm32 \
                        -S ${WORKSPACE}
                '''
            }
        }

        stage('Build') {
            steps {
                echo '========================================='
                echo 'Build'
                echo '========================================='
                sh '''
                    cmake --build ${WORKSPACE}/build/stm32 \
                        -j$(nproc)
                '''
            }
        }
    }

    post {
        success {
            echo '========================================='
            echo 'Build completed successfully'
            echo '========================================='
            archiveArtifacts artifacts: 'build/stm32/**/*.elf, build/stm32/**/*.bin'
        }

        always {
            echo '========================================='
            echo 'Cleaning up workspace...'
            echo '========================================='
            sh 'rm -rf build/obj build/tmp || true'
        }
    }
} 