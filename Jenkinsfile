#!groovy
@Library('hello-jenkins') _

def tools = new org.foo.tools()


pipeline {
    agent any
    environment {
        username = "zhangsan"
        password = "zhagnsan123"
    }
    stages {
        stage("one step") {
            steps {
                echo "todo-one"
                script {
                    // 调用共享库中vars目录下的文件
                    bar()
                }
            }
        }
        stage("tow step") {
            steps {
                echo "todo-tow"
                echo "${username}"
                echo "${password}"
            }
        }
        stage("three step") {
            steps {
                echo "todo-three"
                script {
                    tools.PrintMsg("xxxxxx")
                }
            }
        }
    }
    post {
        always {
            script {
                println("always")
            }
        }
        success {
            script {
                currentBuild.description = "build success"
            }
        }
        failure {
            script {
                currentBuild.description = "build  failure"
            }
        }
        aborted {
            script {
                currentBuild.description = "aborted build"
            }
        }
    }
}

