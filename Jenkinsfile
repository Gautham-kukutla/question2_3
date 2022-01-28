pipeline {
	agent any

  stages {
	  stage('Building'){
		  steps{
	    
	cmakeBuild buildDir: 'build', installation: 'InSearchPath', steps: [[withCmake: true]]
		   }  }
	  stage('Cppcheck'){
		  steps{
			   
			   bat "cppcheck --xml --xml-version=2 . 2> cppcheck.xml"
			 
			  
			  publishCppcheck allowNoReport: true, pattern: 'cppcheck.xml'
		  }}
  }
}

