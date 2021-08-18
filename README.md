# CDK
Inital Install of CDK with typescript

Article is created using AWS Knowledge base https://docs.aws.amazon.com/cdk/latest/guide/hello_world.html


1. If you wish to create a virtual environment then execute below step or you can skip this step and go for step 2
```
python3 -m venv .env
source .env/bin/activate   ## This will activate your Virtual environment.
```

2. Install CDK 
Make sure your working directory is empy of you can create new directory if requried 
```
npm install -g aws-cdk
```

3. Initialize the app using the cdk init command,
```
cdk init app --language typescript
```

#App can be replaced by your application name.

4. Build the app (Its not necessary to compile as CDK take care of it)
```
npm run build
```
5. List the stacks in the app
```
cdk ls
```

#Lets Create S3 Bucket with CDK.
6. Importing the S3 bucket module in CDK
```
npm install @aws-cdk/aws-s3
```

7. Below is the Code from 
_**lib/<your directoryname>-stack.ts  _**
```
import * as cdk from '@aws-cdk/core';
import * as s3 from '@aws-cdk/aws-s3';
export class TestCdkStack extends cdk.Stack {
  constructor(scope: cdk.Construct, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    // The code that defines your stack goes here
    new s3.Bucket(this, 'test-bucket-rahul',{
      versioned: true,
      removalPolicy: cdk.RemovalPolicy.DESTROY,
      autoDeleteObjects: true
    });
  }
}
```

  lets understand what are the parameters used 
**scope:** Tells the bucket that the stack is its parent: it is defined within the scope of the stack. You can define constructs inside of constructs, creating a hierarchy (tree).

**Id:** The logical ID of the Bucket within your AWS CDK app. This (plus a hash based on the bucket's location within the stack) uniquely identifies the bucket across deployments so the AWS CDK can update it if you change how it's defined in your app. Buckets can also have a name, which is separate from this ID (it's the bucketName property).

**props:** A bundle of values that define properties of the bucket. Here we've defined only one property: versioned, which enables versioning for the files in the bucket.


