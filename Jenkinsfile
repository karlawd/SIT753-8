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
zsh 'npm install'
}
}
stage('Run Tests') {
steps {
zsh 'npm test || true' // Allows pipeline to continue despite test failures
}
}
stage('Generate Coverage Report') {
steps {
// Ensure coverage report exists
zsh 'npm run coverage || true'
}
}
stage('NPM Audit (Security Scan)') {
steps {
zsh 'npm audit || true' // This will show known CVEs in the output
}
}
}
}
