pipeline {
    agent {
        docker {
            image 'python:3.10'
        }
    }

    stages {
        stage('Build') {
            steps {
                echo 'Memulai tahap Build: Membuat virtual environment dan menginstal dependensi Python...'

                sh 'python -m venv venv'

                sh '''
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''

                echo 'Tahap Build selesai.'
            }
        }

        stage('Test') {
            steps {
                echo 'Memulai tahap Test: Menjalankan aplikasi Python utama...'

                sh '''
                    . venv/bin/activate
                    python main.py
                '''

                echo 'Tahap Test selesai.'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Memulai tahap Deploy: Mensimulasikan deployment...'
                echo 'Proyek Python-Project berhasil di-deploy (simulasi)!'
                echo 'Tahap Deploy selesai.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline selesai dieksekusi.'
        }
        success {
            echo 'Selamat! Pipeline berhasil diselesaikan.'
        }
        failure {
            echo 'Oops! Pipeline gagal. Periksa Console Output untuk detail.'
        }
    }
}
