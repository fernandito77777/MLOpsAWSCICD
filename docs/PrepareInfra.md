## Launch SageMaker Studio and Prepare Infrastructure

1. Go to [SageMaker Console](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/)
2. click `Amazon SageMaker Studio`
3. click `Standard Setup` and choose `AWS Identity and Access Management (IAM)`

    ![](../images/PrepareInfra/3.png)

4. in Permission, click `Create a new role`
5. In specifying S3 bucket, leave it as default and click `create role`. Make sure you write down the name of your role.
6. Click Submit

    ![](../images/PrepareInfra/6.png)


This might take a while to run. While waiting, now we are going to try to deploy our infrastructure template using CloudFormation

7. Please [click here](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateUrl=https%3A%2F%2Famazon-sagemaker-safe-deployment-pipeline.s3.amazonaws.com%2Fstudio.yml&stackName=mlops-studio&param_PipelineBucket=amazon-sagemaker-safe-deployment-pipeline) To deploy the template. It will bring you to the AWS CloudFormation Console.
8. in `SageMakerStudioRoleName`, Copy the SageMaker studio role you have created in (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
9. Please check the checkbox on Capabilities iAM
10. Click `Create Stack`

    ![](../images/PrepareInfra/10.png)


This might take a while to run. Meanwhile, let's create a user for your sagemaker studio

11. Go to [SageMaker Console](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/landing) and click `Amazon SageMaker Studio`
12. in your SageMaker Studio Control Panel, click `Add user`

    ![](../images/PrepareInfra/12.png)

13. in user name, fill your name.
14. in Execution role, choose the sagemaker role you have created (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
15. click `Submit`

    ![](../images/PrepareInfra/15.png)

once you create the account, now let's try to open the studio.

16. click `Open Studio`

    ![](../images/PrepareInfra/16.png)

This will take a while, since it needs to initialize the studio that we are going to use. Now, during waiting, let's try to give some required permission to the role.

17. Go to [IAM Console](https://console.aws.amazon.com/iam/home?region=us-east-1#)
18. click `Roles`
19. find your role in search bar by typing your sagemaker role name (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
20. click the role name.

    ![](../images/PrepareInfra/20.png)

21. In permission tab, click `Attach policies`
22. Search for `CloudFormationFullAccess`
23. check the `AWSCloudFormationFullAccess` policy
24. click `Attach Policy`

Now, remove the constraints that service catalog have

25. go to [Service Catalog]() Console

Once it's done, let's get back to our sagemaker studio. It will create JupyterLab tab on your browser

25. Go to [SageMaker Console](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/landing) and click `Amazon SageMaker Studio`
26. in your user table, click `Open Studio`

It will open a new tab

27. in your sagemaker studio, Click the lowest icon.
28. click `Create project`
29. click `Organization templates`
30. choose `SageMaker Safe Deployment Pipeline`
31. click `Select project template`
32. in project name, fill it with `sagemaker-safe-deployment-proj`
33. change the email address to your email address.
34. click `create project`