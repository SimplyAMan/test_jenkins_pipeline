pipeline {
    agent any
    parameters {
        extendedChoice(
            name:   'branch',
            defaultValue: '',
            description: 'tag name',
            type: 'PT_SINGLE_SELECT',
            groovyScript: """
            def gettags = ("git ls-remote -t https://github.com/tomerb3/supremedevops.git").execute()
               return gettags.text.readLines().collect { it.split()[1].replaceAll('refs/tags/', '').replaceAll("\\\\^\\\\{\\\\}", '')
            """

        )
    }
    stages {
        stage('build') {
            steps {
                echo ${branch}
            }
        }
    }
}