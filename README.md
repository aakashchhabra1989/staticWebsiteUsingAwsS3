# staticWebsiteUsingAwsS3
**use below commands to upload website - **

set myBucket=<bucketName>
aws s3api put-public-access-block --bucket "%myBucket%" --public-access-block-configuration "BlockPublicPolicy=false,RestrictPublicBuckets=false"
aws s3api put-bucket-website --bucket "%myBucket%" --website-configuration file://html/website.json
aws s3api put-bucket-policy --bucket "%myBucket%" --policy file://html/policy.json
cd C:\staticWebsite\html
aws s3 sync . s3://"%myBucket%"

set region=ap-southeast-1
**use one of the below commands to check the website**
echo. && echo You can now access the website using the following URL... && echo http://%mybucket%.s3-website-%region%.amazonaws.com
echo. && echo You can now access the website using the following URL... && echo http://%mybucket%.s3-website.%region%.amazonaws.com
