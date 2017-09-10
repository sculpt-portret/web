#!groovy

/* The #!groovy above set just for IDE editor
 * Jenkins pipeline groovy DSL https://github.com/jenkinsci/pipeline-plugin/blob/master/TUTORIAL.md */

properties([
        parameters([
                string(defaultValue: 'master', description: 'Builder label', name: 'builderLabel')
        ])
])

def builder = params.builderLabel

node(builder) {
    timestamps {
        try {
            stage('Cleanup') {
                deleteDir()
            }
            currentBuild.result = 'SUCCESS'
        } catch (err) {
            currentBuild.result = 'FAILURE'
            println("Error: " + err.getMessage())
            throw err as java.lang.Throwable
        } finally {
             stage('Cleanup') {
                 deleteDir()
             }
        }

    }
}