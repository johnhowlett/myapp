# myapp
A AWS mu Quickstart

mu can you get by <a href="https://github.com/stelligent/mu">mu</a> or see <a href="https://getmu.io">getmu.io</a>

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
Profile -> settings -> developer settings -> personal assecc tokens

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
Show the status of the service
```bash
➜  myapp git:(master) mu svc show
Unable to load mu config: yaml: unmarshal errors:
  line 6: field haelthEndpoint not found in type common.Service

Pipeline URL:	https://console.aws.amazon.com/codesuite/codepipeline/pipelines/mu-myapp/view?region=eu-central-1
+------------+----------+------------------------------------------+-------------+---------------------+
|   STAGE    |  ACTION  |                 REVISION                 |   STATUS    |     LAST UPDATE     |
+------------+----------+------------------------------------------+-------------+---------------------+
| Source     | Source   | 49c73ef6193513530b95800253fb6c3fe125304a | Succeeded   | 2019-04-30 14:11:30 |
| Build      | Artifact |                                        - | Succeeded   | 2019-04-30 14:12:04 |
| Build      | Image    |                                        - | Succeeded   | 2019-04-30 14:13:08 |
| Acceptance | Deploy   |                                        - | InProgress  | 2019-04-30 14:13:08 |
| Acceptance | Test     |                                        - | -           |                   - |
| Production | Approve  |                                        - | -           |                   - |
| Production | Deploy   |                                        - | -           |                   - |
| Production | Test     |                                        - | -           |                   - |
+------------+----------+------------------------------------------+-------------+---------------------+

Deployments:
+-------------+----------+------------------+---------------------+
| ENVIRONMENT | REVISION |      STATUS      |     LAST UPDATE     |
+-------------+----------+------------------+---------------------+
| acceptance  | 0ecd75a  | CREATE_COMPLETE  | 2019-04-30 13:54:42 |
| production  | 0ecd75a  | CREATE_COMPLETE  | 2019-04-30 13:54:42 |
+-------------+----------+------------------+---------------------+
```
