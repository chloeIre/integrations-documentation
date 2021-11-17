# How to connect S3
For Weld to be able to connect to an S3 bucket. We need a user with the right credentials. <br>
<br>
To connect to a bucket called `weld-sync-destination` you will need to create that bucket in S3. And then you need to add the following policy to a user:<br>
<br>
    {<br>
        "Version": "2012-10-17",<br>
        "Statement": [<br>
            {<br>
                "Effect": "Allow",<br>
                "Action": [<br>
                    "s3:ListBucket",<br>
                    "s3:PutObject",<br>
                    "s3:PutObjectAcl"<br>
                ],<br>
                "Resource": [<br>
                    "arn:aws:s3:::weld-sync-destination",<br>
                    "arn:aws:s3:::weld-sync-destination/*"<br>
                ]<br>
            }<br>
        ]<br>
    }<br>
<br>
When you have created that user. Then you need to pick up the `AWS Access Key Id` and `AWS Secret Access Key` and input them in the form along with the bucket name.<br>
<br>
The S3 integration will run a small test that tries to put a text file in the bucket that you have specified. If everything is correct the connection will be accepted.<br>