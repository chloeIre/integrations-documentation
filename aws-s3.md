# How to connect S3
For Weld to be able to connect to an S3 bucket. We need a user with the right credentials.   
  
To connect to a bucket called `weld-sync-destination` you will need to create that bucket in S3. And then you need to add the following policy to a user. It is important that you create a new user for this. And only attach this policy to that user. This ensures that Weld can only push objects into S3 and helps secure your AWS account.
  
    {  
        "Version": "2012-10-17",  
        "Statement": [  
            {  
                "Effect": "Allow",  
                "Action": [  
                    "s3:ListBucket",  
                    "s3:PutObject",  
                    "s3:PutObjectAcl"  
                ],  
                "Resource": [  
                    "arn:aws:s3:::weld-sync-destination",  
                    "arn:aws:s3:::weld-sync-destination/*"  
                ]  
            }  
        ]  
    }  
  
When you have created that user. Then you need to pick up the `AWS Access Key Id` and `AWS Secret Access Key` and input them in the form along with the bucket name.  
  
The S3 integration will run a small test that tries to put a text file in the bucket that you have specified. If everything is correct the connection will be accepted.  
