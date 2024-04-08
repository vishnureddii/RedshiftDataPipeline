# RedshiftDataPipeline
The main goal of this project is to transfer Natality data(.CSV file) from S3 bucket through AWS Glue to Amazon Redshift for data storage and analysis purpose.
The platform’s goals are to:
Identify Factors: Determine the critical factors that contribute to fluctuations in baby weights.
Prioritize Care: Offer insights that aid in the strategic placement of antenatal care units.
Visualize Data: Create interactive dashboards on QuickSight to display insights derived from the data.
Initially I created a bucket and uploaded natality.csv object into my S3 bucket.
Firstly before creating a cluster in redshift, we need to create a VPC endpoint and edit few security group in-bound rules for succesful execution.
Now I created a glue Crawler in AWS Glue to extract natality.csv file data from S3, for that I created an IAM role with AmazonS3ReadOnlyAccess Bucket and RedshiftFullAccess policies to it, and also created a temporary data for Glue to store metadata of that natality.csv file.
Now I created a 1 free-tier cluster using Amazon Redshift service, and connected the database which created during the creation of workgroup and namespace.
Now again coming back to AWS Glue, when crawler run is succeeded, go to database and check for the metadata of that table.
Then after create new crawler to load data from AWS Glue to redshift. Now set IAM role(GlueconsoleFullaccess) to that crawler to view the metadata of that table that is this role should has bidirectional access Glue to redshift and vice-versa
Now create a visual ETL job, to set a destination for loading this data. Once if we created all settings, run this job then you can observe the mapping between the two crawlers metadata.
Now go to redshift editor and check the Database connection once again and start querying to get the data from AWS Glue to redshift. In this redshift we can use this for storage purpose or to analyze the data.
Now these analysis can be visualized using AWS Quicksight which is a visualizing tool avaliable in AWS.
These can be acheived by establishing the connection between Redshift and Quicksight.

FEW OUTPUT FILES ARE ATTACHED ABOVE

