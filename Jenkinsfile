// Jenkinsfile
// Ini adalah script Jenkins Pipeline yang akan dijalankan.

pipeline {
    agent any // Jenkins akan menjalankan pipeline ini di agen (server) manapun yang tersedia.

    // Bagian 'stages' mendefinisikan tahapan-tahapan utama pipeline kita.
    stages {
        // --- Tahap 1: Build ---
        // Di tahap ini, kita menyiapkan lingkungan dan dependensi proyek.
        stage('Build') {
            steps {
                echo 'Memulai tahap Build: Membuat virtual environment dan menginstal dependensi Python...'

                // Perintah untuk membuat virtual environment Python
                // Gunakan python3 jika python saja tidak dikenali di sistem Jenkins agent
                sh 'python3 -m venv venv'

                // Perintah untuk mengaktifkan virtual environment dan menginstal dependensi
                // dari file 'requirements.txt' yang sudah kamu perbaiki namanya.
                sh 'source venv/bin/activate && pip install -r requirements.txt'

                echo 'Tahap Build selesai.'
            }
        }

        // --- Tahap 2: Test ---
        // Di tahap ini, kita menjalankan pengujian otomatis.
        // Karena kamu punya main.py, kita akan menjalankannya sebagai tes dasar.
        stage('Test') {
            steps {
                echo 'Memulai tahap Test: Menjalankan aplikasi Python utama...'

                // Aktifkan kembali virtual environment.
                sh 'source venv/bin/activate'

                // Jalankan file utama proyekmu, yaitu main.py
                sh 'python3 main.py'

                // Jika di masa depan kamu menambahkan unit test (misal dengan pytest),
                // kamu bisa mengganti 'python3 main.py' dengan 'pip install pytest && pytest'.

                echo 'Tahap Test selesai.'
            }
        }

        // --- Tahap 3: Deploy ---
        // Tahap ini untuk menyebarkan aplikasi. Untuk pemula, ini bisa disimulasikan.
        stage('Deploy') {
            steps {
                echo 'Memulai tahap Deploy: Mensimulasikan deployment...'
                echo 'Proyek Python-Project berhasil di-deploy (simulasi)!'
                echo 'Tahap Deploy selesai.'
            }
        }
    }

    // Bagian 'post' akan dijalankan setelah semua 'stages' selesai.
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
