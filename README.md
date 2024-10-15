# AWS-Minecraft-mod-server-Lost-Souls-
Full guide to launch server on AWS. using Lost souls package

So, for start we need: 
  - Minecraft server with mods (If you want take only mods, you can unzip it on your pc).
  - Aws account
  - Money(1h)
  - Client version
## Installation
1. Download the server https://drive.google.com/file/d/1hmCBF0D21vmju5k1kfSkkZ6kIBxumrQe/view?usp=sharing
2. Download the client version to play https://drive.google.com/file/d/1w7za65ggwPNBAnRpQBYoUPBThEGE9MyW/view?usp=drive_link

## AWS Configuration
1.AWS IAM role creation.
For further interaction we need role in AMI system, it will help us in the future. 
(To get this page, enter IAM in the search bar, and in the left panel choose 'policies') 
![изображение](https://github.com/user-attachments/assets/fa05a26d-d45e-4e6b-aa47-c65254078c81)
Name it to easy find (for example, "Minecraft-loader-policy")
In policy editor just paste this code 
![изображение](https://github.com/user-attachments/assets/61802dc7-9577-44a3-8053-bf5e80a6716b)

```uml
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::minecraftmods-lost-souls"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject",
                "s3:GetBucketLocation",
                "s3:PutObject",
                "s3:PutObjectAcl",
                "s3:DeleteObject"
            ],
            "Resource": [
                "arn:aws:s3:::minecraftmods-lost-souls/*"
            ]
        }
    ]
}
```

1. we need to upload this zip on s3 bucket, let's create it. 
![изображение](https://github.com/user-attachments/assets/30675bb9-3139-4aef-81cc-e0a20cff8584)
Press ```create bucket```
We don't need something special there, just create it. 

We have two ways to send our zip to s3 bucket:
1. Using UI from aws
2. Using AWS CLI
I show both, but having poor internet connection made me to use cli for better speed. (I could solve problem with UI version, but for me was easier to download cli).


 1.1
 Clicking on the name of our s3 bucket, we need to press button "Upload"
 ![изображение](https://github.com/user-attachments/assets/93a1def7-2c7d-4d24-ac27-11626f43ced2)
  Then just drag and drop the zip
 2.1
 





