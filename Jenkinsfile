pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Memulai tahap Build: Membuat virtual environment dan menginstal dependensi Python...'

                // Buat virtual environment
                sh 'python -m venv venv'

                // Aktifkan dan install dependensi (Windows/Linux otomatis cek path)
                sh '''
                    if [ -f "venv/Scripts/activate" ]; then
                        . venv/Scripts/activate
                    else
                        . venv/bin/activate
                    fi
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
                    if [ -f "venv/Scripts/activate" ]; then
                        . venv/Scripts/activate
                    else
                        . venv/bin/activate
                    fi
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
