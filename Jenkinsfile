##
pipeline{
    agent any 
    stages{
        stage("Lint HTML"){
            steps{
                sh '''
                    echo "Linting HTML..."
                    tidy -q -e *.html
                '''
            }
        }
        stage("Upload To AWS"){
            steps{
                withAWS(region:'eu-central-1',credentials:'aws-static'){
                    s3Upload(file:'index.html', bucket:'udacityjenkins', pathStyleAccessEnabled: true, payloadSigningEnabled: true)
                }
            }
        }
        stage("Ensure content is up"){
            steps{
                retry(3){
                sh '''
                        if curl --silent --head --fail "http://udacityjenkins.s3-website.us-west-2.amazonaws.com/"; then \
                            echo "The content is up ... "; \
                            exit 0; \
                        else \
                            echo "This URL Not Exist !!"; \
                            exit 1; \
                        fi 
                '''
            }}
        }
    }
}
