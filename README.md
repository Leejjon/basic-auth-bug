Requirements:
- Git
- AWS CLI
- npm
- yarn (optional)
- cdk
- github account

To run this thing.

- Fork this project on github
- Clone it locally and checkout to the "above2420" branch
- Create a codestar connection in your aws account: https://docs.aws.amazon.com/dtconsole/latest/userguide/connections-create-github.html
- Copy and paste the arn of this codestar connection in line 10 of the deployment.ts
- Create a secret in the secret manager of type other. Enter the key "GithubOauthToken" and value an Personal access token that you need to make on github (Developer Settings -> Personal access tokens)
- Give it a name (in my case "css-secrets") and save it
- Copy the arn of this secret and paste it in line 29 of the web-amplify-stack.ts
- Build the root of the project with yarn install and yarn build (or npm install but then you have to delete the yarn.lock file)
- Browse to the deployment folder and run "npm install" and "npm run build"
- Type "cdk ls" to verify if there are no errors in your cdk code
- I also ran this command but I'm not sure if it was needed: cdk bootstrap aws://accountid/region
- cdk deploy
- Verify that there is a "basic-auth-bug-pipeline" cloudformation template

