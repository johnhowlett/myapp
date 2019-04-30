# myapp
A AWS mu Quickstart

Make the files index.html and the Dockerfile

Initialize the mu.yml and buildspec.yml files: mu init --port 80 --env
```bash
myapp git:(master) ✗ mu init --port 80 --env
```

Update the mu.yaml to use / for the healthEndpoint
```bash
  healthEndpoint: /
```
Enter your GitHub Token when prompted (creation of OAuth GitHub token guide here)


Create the pipeline: mu pipeline up
```bash
➜  myapp git:(master) mu pipeline up
Unable to load mu config: yaml: unmarshal errors:
  line 6: field haelthEndpoint not found in type common.Service
CodePipeline requires a personal access token from GitHub - https://github.com/settings/tokens
  GitHub token: : ****************************************

Upserting Bucket for CodeDeploy
Upserting Bucket for CodePipeline
  Created stack 'mu-bucket-codepipeline'
  Created stack 'mu-bucket-codedeploy'
Upserting IAM resources
  Created stack 'mu-iam-common'
  Created stack 'mu-iam-environment-production'
  Created stack 'mu-iam-service-myapp-acceptance'
  Created stack 'mu-iam-service-myapp-production'
  Created stack 'mu-iam-environment-acceptance'
  Created stack 'mu-iam-pipeline-myapp'
|Upserting Pipeline for service 'myapp' ...
  Created stack 'mu-pipeline-myapp'
```
