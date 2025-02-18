# Amazon EC2: Allows starting or stopping EC2 instances a user has tagged, programmatically and in the console<a name="reference_policies_examples_ec2_tag-owner"></a>

This example shows how you might create an IAM policy that allows an IAM user to start or stop EC2 instances, but only if the instance tag `Owner` has the value of that user's user name\. This policy defines permissions for programmatic and console access\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "ec2:StartInstances",
                "ec2:StopInstances"
            ],
            "Resource": "arn:aws:ec2:*:*:instance/*",
            "Condition": {
                "StringEquals": {
                    "aws:ResourceTag/Owner": "${aws:username}"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": "ec2:DescribeInstances",
            "Resource": "*"
        }
    ]
}
```