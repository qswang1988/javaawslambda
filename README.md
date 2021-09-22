# javaawslambda
Tutorial for creating AWS lambda function in Java

step 1. Get your local AWS CLI and credentials prepared https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-welcome.html

step 2. Get your IAM role with LAMBDA authorized.

step 3. run 'mvc package' in terminal, and check jar files under folder 'target'.

step 4. create aws lambda function.

command: 
aws lambda create-function --function-name [LAMBDA FUNCTION NAME] --zip-file fileb://[JAR FILE NAME] --runtime [JAVA VERSION,e.g: java11] --handler [PackageName.ClassName]::[JavaMethodName] --timeout 10 --memory-size 128 --role [IAM Role ARN] --region '[Region]' --profile [Profile Name]

example: 
aws lambda create-function --function-name func2 --zip-file fileb://javalambda-1.0-SNAPSHOT.jar --runtime java11 --handler org.example.Handler::handleRequest --timeout 10 --memory-size 128 --role arn:aws:iam::550120278025:role/qswLambdaBasicRole --region 'eu-north-1' --profile wang-cli

step 5. check if the function was created. If yes, try invoke it in CLI

example: 
aws lambda invoke --function-name func2 --region 'eu-north-1' result.json --profile wang-cli && cat result.json
