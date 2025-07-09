pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-bookworm' // ✅ Use full Debian-based image
                    reuseNode true
                }
            }

            steps {
                sh '''
                    echo "📁 Listing workspace contents:"
                    ls -la

                    echo "🧪 Node & npm versions:"
                    node --version
                    npm --version

                    echo "🧹 Cleaning npm cache:"
                    npm cache clean --force

                    echo "📦 Installing dependencies:"
                    npm install  # Use this instead of npm ci for now

                    echo "🏗️ Building the app:"
                    npm run build

                    echo "✅ Build complete. Listing output:"
                    ls -la
                '''
            }
        }
    }
}
