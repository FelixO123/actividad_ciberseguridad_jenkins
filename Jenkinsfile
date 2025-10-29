pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Compilando el código fuente...'
                sh 'python3 -m py_compile app.py'
            }
        }

        stage('Test') {
            steps {
                echo 'Ejecutando pruebas unitarias...'
                sh 'pytest --maxfail=1 --disable-warnings -q'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Desplegando aplicación en entorno de prueba...'
                sh 'docker build -t hello-jenkins-app .'
                sh 'docker run -d -p 5000:5000 hello-jenkins-app'
            }
        }
    }
}

