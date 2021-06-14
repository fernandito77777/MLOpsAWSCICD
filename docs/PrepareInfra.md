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

7. Please [click here in new tab](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateUrl=https%3A%2F%2Famazon-sagemaker-safe-deployment-pipeline.s3.amazonaws.com%2Fstudio.yml&stackName=mlops-studio&param_PipelineBucket=amazon-sagemaker-safe-deployment-pipeline) To deploy the template. It will bring you to the AWS CloudFormation Console.
8. in `SageMakerStudioRoleName`, Copy the SageMaker studio role you have created in (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
9. Please check the checkbox on Capabilities iAM
10. Click `Create Stack`

    ![](../images/PrepareInfra/10.png)


This might take a while to run. Meanwhile, let's give the user permission for Service Catalog. Service catalog is containing the template for our Machine Learning environment.

11. Go to [IAM Console](https://console.aws.amazon.com/iam/home?region=us-east-1#)
12. click `Roles`
13. find your role in search bar by typing your sagemaker role name (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
14. click the role name.

    ![](../images/PrepareInfra/14.png)

15. In permission tab, click `Attach policies`
16. Search for `AWSServiceCatalogAdminFullAccess`
17. check the `AWSServiceCatalogAdminFullAccess` policy
18. click `Attach Policy`

    ![](../images/PrepareInfra/18.png)

Now, remove the constraints that service catalog have

25. go to [Service Catalog Console](https://console.aws.amazon.com/servicecatalog/home?region=us-east-1#portfolios?activeTab=localAdminPortfolios)
26. click your Local Portofolios

    ![](../images/PrepareInfra/26.png)

27. click `Constraints` tab
28. click the radio button besides the constraints
29. click `Delete constraint`

    ![](../images/PrepareInfra/29.png)

30. Type `delete` and click `delete` button.

Once it's done, let's go back to the SageMaker.

31. Go to [SageMaker Console](https://console.aws.amazon.com/sagemaker/home?region=us-east-1#/landing) and click `Amazon SageMaker Studio`
32. in your SageMaker Studio Control Panel, click `Add user`

    ![](../images/PrepareInfra/32.png)

33. in user name, fill your name.
34. in Execution role, choose the sagemaker role you have created (The one that looks like `AmazonSageMaker-ExecutionRole-<random-numbers-here>`)
35. click `Submit`

    ![](../images/PrepareInfra/35.png)

once you create the account, now let's try to open the studio.

16. click `Open Studio`

    ![](../images/PrepareInfra/36.png)

It will open a new tab. This will take a while, since it needs to initialize the studio that we are going to use.

37. in your sagemaker studio, Click the lowest icon.
38. click `Create project`
39. click `Organization templates`
40. choose `SageMaker Safe Deployment Pipeline`
41. click `Select project template`

    ![](../images/PrepareInfra/41.png)

42. in project name, fill it with `sagemaker-safe-deployment-proj`

    ![](../images/PrepareInfra/42.png)

43. change the email address to your email address.
44. click `create project`

We need to wait for a while. This runs cloudformation stack behind the scene, taken from service catalog.

45. click `Clone repo`

    ![](../images/PrepareInfra/45.png)

46. in clone repository page, click `Clone Repository`
47. once the clone is done, click the top icon, and click `notebook` folder

    ![](../images/PrepareInfra/47.png)

48. click `mlops.ipynb` file
49. in select kernel page, choose `Python 3 (Data Science)` and click `Select`
50. in importing packages, please include this code

    

    You can copy this code to add it to your notebook.

```
!{sys.executable} -m pip install seaborn --upgrade
```

We need the service catalog name that has been deployed.

51. go to [Service Catalog Console](https://console.aws.amazon.com/servicecatalog/home?region=us-east-1#provisioned-products)
52. in provisioned products, change the filter to `Account`
53. copy the name of your project (similar to `sagemaker-safe-deployment-proj-<random-strings>`)
    ![](../images/PrepareInfra/53.png)

54. paste it into `PROJECT_NAME` in your notebook
    ![](../images/PrepareInfra/54.png)

55. please go to the next step by following the instruction on notebook by reffering to Data Prep [Here](https://mlops-safe-deployment-pipeline.workshop.aws/01_data_prep.html)

[BACK TO WORKSHOP GUIDE :house:](../README.md)