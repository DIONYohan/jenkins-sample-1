timestamps {

node () {

               stage ('App-IC - Checkout') {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'yohan.id', url: 'https://github.com/DIONYohan/jenkins-sample-1.git']]]) 
               }
               stage ('App-IC - Build') {
                                           // Maven build step
               withMaven(maven: 'maven') { 
                                            if(isUnix()) {
                                                          sh "mvn clean package " 
                                            } else { 
                                                           bat "mvn clean package " 
                                            } 
                              }                            // Maven build step
               withMaven(maven: 'maven') { 
                                            if(isUnix()) {
                                                          sh "mvn sonar:sonar " 
                                            } else { 
                                                           bat "mvn sonar:sonar " 
                                            } 
                              } 
               }
}
}
