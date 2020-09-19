pipeline {
agent any
stage('Upload to AWS') {
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
