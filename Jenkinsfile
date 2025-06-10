// Jenkinsfile
// Ini adalah script Jenkins Pipeline yang akan dijalankan.

pipeline {
    // 'agent any' berarti Jenkins akan menjalankan pipeline ini di agen (server) manapun yang tersedia.
    agent any

    // Bagian 'stages' mendefinisikan tahapan-tahapan utama pipeline kita.
    stages {
        // --- Tahap 1: Build ---
        // Di tahap ini, kita menyiapkan lingkungan dan dependensi proyek.
        stage('Build') {
            steps {
                echo 'Memulai tahap Build: Menginstal dependensi Python...'

                // Perintah untuk membuat virtual environment Python
                // Virtual environment akan mengisolasi dependensi proyekmu dari sistem global.
                sh 'python3 -m venv venv' // Gunakan python3 jika python saja tidak dikenali

                // Perintah untuk mengaktifkan virtual environment dan menginstal dependensi
                // Asumsikan kamu memiliki file 'requirements.txt' di root proyekmu.
                // Jika tidak, kamu bisa menginstal library satu per satu, misalnya:
                // sh 'source venv/bin/activate && pip install flask'
                sh 'source venv/bin/activate && pip install -r requirements.txt'

                echo 'Tahap Build selesai.'
            }
        }

        // --- Tahap 2: Test ---
        // Di tahap ini, kita menjalankan pengujian otomatis untuk memastikan kode berfungsi dengan baik.
        stage('Test') {
            steps {
                echo 'Memulai tahap Test: Menjalankan unit tests...'

                // Pastikan virtual environment diaktifkan kembali.
                sh 'source venv/bin/activate'

                // Contoh: Menginstal pytest (jika belum ada di requirements.txt) dan menjalankan tes
                // Jika proyekmu menggunakan metode tes lain (misalnya unittest bawaan Python),
                // sesuaikan perintah 'sh' di bawah ini.
                sh 'pip install pytest' // Instal pytest jika belum ada
                sh 'pytest' // Jalankan tes dengan pytest. Pastikan kamu punya file tes, misalnya test_*.py

                // Jika proyekmu tidak punya tes formal tapi ada script untuk dijalankan,
                // kamu bisa mengganti 'pytest' dengan menjalankan script utamamu:
                // sh 'python main.py' // atau nama file utama proyekmu
                // TAPI, lebih disarankan punya unit test untuk validasi.

                echo 'Tahap Test selesai.'
            }
        }

        // --- Tahap 3: Deploy ---
        // Tahap ini untuk menyebarkan aplikasi. Untuk pemula, ini bisa disimulasikan.
        stage('Deploy') {
            steps {
                echo 'Memulai tahap Deploy: Mensimulasikan deployment...'

                // Untuk tugas ini, kita bisa mensimulasikan deployment.
                // Jika kamu memiliki server atau layanan hosting, langkah ini akan jauh lebih kompleks
                // (misalnya, menggunakan SSH, Docker, atau integrasi dengan penyedia cloud).
                // Untuk saat ini, kita anggap sukses jika sampai sini.
                echo 'Proyek Python-Project berhasil di-deploy (simulasi)!'

                echo 'Tahap Deploy selesai.'
            }
        }
    }

    // Bagian 'post' akan dijalankan setelah semua 'stages' selesai,
    // terlepas dari apakah pipeline berhasil atau gagal.
    post {
        always {
            // Memberi tahu status akhir pipeline
            echo 'Pipeline selesai dieksekusi.'
        }
        success {
            echo 'Selamat! Pipeline berhasil diselesaikan.'
            // Contoh: Mengirim notifikasi email jika sukses
            // mail to: 'your-email@example.com', subject: 'Jenkins Pipeline Success!'
        }
        failure {
            echo 'Oops! Pipeline gagal. Periksa Console Output untuk detail.'
            // Contoh: Mengirim notifikasi email jika gagal
            // mail to: 'your-email@example.com', subject: 'Jenkins Pipeline FAILED!'
        }
    }
}
