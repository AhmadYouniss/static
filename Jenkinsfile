pipeline {
agent any
stage('Build') {
steps {
sh 'echo "Hello world"'
sh '''
echo "multiline shell steps work too"
ls -lah
'''
}
}
}
}
