# CI CD for Serverless - AWS CodePipeline Integration

 If you have a team of developers that are constantly merging branches back into master and you want to set up automated testing and deployment using a Continuous Integration/Continuous Deployment (CICD) toolchain

> AWS CodePipeline is a fully managed continuous delivery service
> that helps you automate your release pipelines for 
> fast and reliable application and infrastructure updates.
> CodePipeline automates the build, test, and deploy phases of your release process
> every time there is a code change, based on the release model you define
> This enables you to rapidly and reliably deliver features and updates.
> You can easily integrate AWS CodePipeline with third-party services such as GitHub or with your own custom plugin.
> With AWS CodePipeline, you only pay for what you use. 
> There are no upfront fees or long-term commitments.

### CI-CD Architecture Using CodePipeline

[![N|Solid](https://s3.amazonaws.com/analyzer.fmlnerd.com/img/ServerlessCICDmed.png)](https://nodesource.com/products/nsolid)

### If you are new to CI and CD 
> At a high level the CI-CD thing looks like this:

[![N|Solid](https://s3-us-west-2.amazonaws.com/assets.blog.serverless.com/cicd/cicd-process.gif)](https://nodesource.com/products/nsolid)


## Pipeline Structure

When this application is deployed, it will create an AWS CodePipeline pipeline that has up to the following 5 stages:
1. **Source**: This stage is the entry point of the pipeline. It is triggered when you push a change to the specified Git repository branch.
1. **Build**: This stage builds the project using AWS CodeBuild.
1. **Test** (optional): This stage runs the integration tests of the project using CodeBuild. This stage will only be created if you provide the `IntegTestRoleName` parameter when setting up this module.
1. **Deploy** (optional): This stage deploys the project using CloudFormation. This stage will only be created if you provide the `DeployRoleName` parameter when setting up this application.
1. **Publish** (optional): This stage publishes the project to AWS Serverless Application Repository using the publish


##### Here is an example CodePipeline pipeline that has all 5 stages.
.
![aws-sam-codepipeline-cd-pipeline-example](https://github.com/awslabs/aws-sam-codepipeline-cd/raw/master/images/aws-sam-codepipeline-cd-pipeline-example.png)
