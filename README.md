# H1 Creating a Static Website Using Amazon S3
## H2 Introduction
In this live AWS hands-on lab, we will create and configure a simple static website. We will go through configuring that static website with a custom error page. This will demonstrate how to create a very cost-efficient website hosting for sites that consist of files like HTML, CSS, JavaScript, fonts, and images.
Solution
Log in to the live AWS environment using the credentials provided. Make sure you're in the N. Virginia (us-east-1) region throughout the lab.
The code for the static site is in git.
**Create S3 Bucket**
1.	Navigate to S3.
2.	Click Create bucket.
3.	Give it a globally unique name (e.g., "my-bucket-" with the AWS account number or another series of numbers at the end).
4.	Select the US East (N. Virginia) region.
5.	In the Bucket settings for Block Public Access section, un-check Block all public access and then un-check all four permissions restrictions under it.
Note: If you skip this step, the bucket policy will have no effect.
6.	Leave the rest of the settings as their defaults.
7.	Click Create bucket.
8.	Select the bucket name.
9.	Click Upload.
10.	Click Add files, and upload your own or those from the lab GitHub repo .
11.	Click Upload.
Enable Static Website Hosting
1.	Click the Properties tab.
2.	Click the Static website hosting card.
3.	Select Use this bucket to host a website.
4.	For Index document, enter index.html.
5.	For Error document, enter error.html.
6.	Click Save.
7.	Click the Static website hosting card again.
8.	Click the listed endpoint URL. We'll see an AccessDenied error message.
Apply Bucket Policy
1.	Back in S3, click the Permissions tab.
2.	Click Bucket Policy.
3.	In the Bucket policy editor box, enter the following JSON statement (replacing <my-bucket> with your bucket name):

```
{
  "Version":"2012-10-17",
  "Statement":[{
     "Sid":"PublicReadGetObject",
     "Effect":"Allow",
     "Principal": "*",
     "Action":["s3:GetObject"],
     "Resource":["arn:aws:s3:::<my-bucket>/*"]
  }]
}
```

Note: Ensure the trailing /* is present so the policy applies to all objects within the bucket.
4.	Refresh the browser tab with the static website. This time, it should load the site correctly.
5.	Add a / at the end of the URL and some random letters (anything that's knowingly an error). This will display our error.html info.
Conclusion
Congratulations on completing this hands-on lab!
