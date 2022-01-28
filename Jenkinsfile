pipeline {
	agent any

  stages {
	  stage('Building'){
		  steps{
	    
	cmakeBuild buildDir: 'build', installation: 'InSearchPath', steps: [[withCmake: true]]
		   }  }
	  stage('Cppcheck'){
		  steps{
			   bat '''#!/bin/bash
			   cppcheck --xml --xml-version=2 . 2> cppcheck.xml'''
			  scanForIssues tool: cppCheck(pattern: 'cppcheck.xml')
			  
			  publishCppcheck allowNoReport: true, pattern: 'cppcheck-result.xml'
		  }}
  }
}

