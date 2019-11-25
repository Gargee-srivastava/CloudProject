# CloudProject
Managing secrets securely


**The basic functions implemented are:**

-new user creation, an email is sent to validate the email address provided

-login, getting back an authentication "token" that can be used with Amazon Cognito to assume an Authenticated Role via -Developer Authenticated Identities

-password change

-password reset, an email is sent with a link to reset the password

-Store login credentials securely in Vault(HASHI-CORP Vault)

-Ensure that passwords meet complexity requirements

-replicate datas on multiple clouds.

**Passwords are not saved in clear in the database, but "salted" (via HMAC-SHA1) using a dedicated, random salt for each password.

Login page hosted on Amazon S3 bucket

![login](https://user-images.githubusercontent.com/39323310/69563917-06396a00-0fd8-11ea-86e5-00392b9f39fc.png)



**Resources used:**

1.the Amazon S3 bucket to host the sample HTML pages

2.the Amazon DynamoDB table for users and credentials

3.the AWS Identity and Access Management (IAM) roles for Amazon Cognito and AWS Lambda

4.the Amazon Cognito identity pool

5.HashiCorp Vault cluster that is reachable from your server instances. (Inbound TCP port 8200 to Vault)

6.Depsky for multiple cloud replication(amazon and azure used here)

![dynamic-secret](https://user-images.githubusercontent.com/39323310/69564571-3e8d7800-0fd9-11ea-89e4-cc375c381055.jpg)

**APIs**

1.LambdAuthCreateUser	- email, password	created: true / false

2.LambdAuthVerifyUser	- email, verify	verified: true / false

3.LambdAuthLogin	- email, password	login: true / false, identityId, token

4.LambdAuthChangePassword	- email, oldPassword, newPassword	changed: true / false

**Password Rotation policy:**

![2days](https://user-images.githubusercontent.com/39323310/69564638-611f9100-0fd9-11ea-9737-3b0d88a39e22.png)

![14days](https://user-images.githubusercontent.com/39323310/69564678-71d00700-0fd9-11ea-9d93-2c338d76d23f.png)
![schedtask](https://user-images.githubusercontent.com/39323310/69564702-7f858c80-0fd9-11ea-98dd-d1c4d34294d3.png)


