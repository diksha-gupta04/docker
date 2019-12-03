node('docker')
 {
	stage 'Checkout'
		checkout scm
	stage 'Build & Unittest'
		sh "docker build -t myimage:B${BUILD_NUMBER} -f Dockerfile ."
 }
 
