pipeline {
	agent any

  stages {
	  stage('Building'){
		  steps{
	    
	cmakeBuild buildDir: 'build', installation: 'InSearchPath', steps: [[withCmake: true]]
		   }  }
	  stage('Cppcheck'){
		  steps{
			   sh '''#!/bin/bash

                    cppcheck --xml --xml-version=2 SOURCE_DIRECTORY 2> cppcheck.xml'''
			  
			  publishCppcheck allowNoReport: true, pattern: 'cppcheck-result.xml'
		  }}
  }
}

