pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-bullseye-slim' // ✅ Use full Debian-based image
                    args '--network=host'
                    reuseNode true
                }
            }

            steps {
                sh '''
                    echo "🧹 Cleaning up node_modules and npm cache..."
                    rm -rf node_modules package-lock.json ~/.npm
                    npm cache clean --force

                    echo "📦 Installing dependencies..."
                    npm install --verbose
                '''

            }
        }
    }
}
