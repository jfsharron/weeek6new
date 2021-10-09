pipeline {
     agent any
     stages {
          stage("Compile") {
               steps {
                    sh "./gradlew compileJava"
               }
             }
          stage("echo branch") {
               steps {
                    echo env.GIT_BRANCH
               }
            }          
		  stage("Unit test") {
               when {
			     branch 'master' 
				}
			   steps {
                    sh "./gradlew test"
               }
             }
          stage("Code coverage") {
               when {
			     branch 'master' 
				}               
			   steps {
                    sh "./gradlew jacocoTestReport"
                    sh "./gradlew jacocoTestCoverageVerification"
               }
             }	
          stage("Static code analysis") {
               when {
			     branch 'master' 
				}
			   steps {
                    sh "./gradlew checkstyleMain"
               }
             }
           }
    }