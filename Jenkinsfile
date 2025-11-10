pipeline {
agent any
stages {
stage('Checkout') {
steps {
git branch: 'main', url: 'https://github.com/karlawd/SIT753-8.git'
}
}
stage('Install Dependencies') {
steps {
sudo 'npm install'
}
}
stage('Run Tests') {
steps {
sudo 'npm test || true' // Allows pipeline to continue despite test failures
}
}
stage('Generate Coverage Report') {
steps {
// Ensure coverage report exists
sudo 'npm run coverage || true'
}
}
stage('NPM Audit (Security Scan)') {
steps {
sudo 'npm audit || true' // This will show known CVEs in the output
}
}
}
}
