
## CloudFormation Template Structure

```yml
AWSTemplateFormatVersion: version date

Description:
  String

Metadata:
  template metadata

Parameters:
  set of parameters

Rules:
  set of rules

Mappings:
  set of mappings

Conditions:
  set of conditions

Transform:
  set of transforms

Resources:
  set of resources

Outputs:
  set of outputs

```

#### ✅ AWSTemplateFormatVersion

```yml
AWSTemplateFormatVersion: 'YYYY-MM-DD'
```

- Specifies the version of the CloudFormation template.
    
- Always use `'2010-09-09'` (most common and current version).

#### ✅ Description

```yml
Description: >
  Description of the stack (what this template does).
```

- Gives a human-readable summary.
    
- Helps other team members or users understand the purpose.


#### ✅ Metadata

```yml
Metadata:
  Authors: [Author Names]
  Team: DevOps / Cloud
  Project: Project Name
```

- Stores extra information like **authors**, **team name**, or **project name**.
    
- Useful for documentation or automation tools.

#### ✅ Parameters

```yml
Parameters:
  # Define user-configurable values like instance types, etc.
  ParamName:
    Type: String
    Default: defaultValue
    Description: Description of the parameter
```

- Allow users to input values **at deployment time**.
    
- Make templates more flexible.
    
- You can define:
    
    - Type (String, Number, etc.)
        
    - Default value
        
    - Allowed values
        
    - Description

#### 🔐 Rules (Optional)

```yml
Rules:
  # Optional rules to validate parameters
  RuleName:
    Assertions:
      - Assert:
          'Fn::Condition': [some condition]
        AssertDescription: Must meet some criteria
```

- Used to **validate parameter values**.
    
- Prevents invalid configurations.
    
- Rarely used by beginners but powerful in large projects.

#### ✅ Mappings

```yml
Mappings:
  # Map parameter values to actual configurations
  MappingName:
    region:
      key: value
```

- Used to define static values based on conditions like AWS Region.
    
- Very useful to map different AMIs for each region.

### ✅ Resources (The Core Part!)

```yml
Resources:
  # Main section for defining AWS resources (EC2, S3, etc.)
  MyResource:
    Type: AWS::Service::ResourceType
    Properties:
      Key: Value
```

- This is **where you define all AWS services** like EC2, S3, RDS, etc.
    
- Every resource has:
    
    - A logical name (`MyS3Bucket`)
        
    - A `Type` (e.g., `AWS::S3::Bucket`)
        
    - A `Properties` section with specific settings

#### ✅ Outputs
```yml
Outputs:
  # Output values after stack creation
  OutputName:
    Description: Info about the output
    Value: !Ref SomeResource
```

-  After the stack is deployed, outputs return useful values like:
    
    - Instance ID
        
    - Bucket name
        
    - Endpoint URLs
        
- These values can be shared with other stacks or users.

## S3 + EC2 CloudFormation Template Structure:

```yml
AWSTemplateFormatVersion: '2010-09-09'

Description: >
  This template creates an EC2 instance and an S3 bucket.

Parameters:
  InstanceType:
    Description: EC2 Instance Type
    Type: String
    Default: t2.micro
    AllowedValues:
      - t2.micro
      - t2.small
      - t3.micro
    ConstraintDescription: Must be a valid EC2 instance type.

Mappings:
  RegionMap:
    us-east-1:
      AMI: ami-0c02fb55956c7d316
    us-west-2:
      AMI: ami-0a91cd140a1fc148a

Resources:
  MyS3Bucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-cft-demo-bucket

  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: !Ref InstanceType
      ImageId: !FindInMap 
        - RegionMap
        - !Ref "AWS::Region"
        - AMI
      Tags:
        - Key: Name
          Value: MyDemoEC2

Outputs:
  EC2InstanceId:
    Description: EC2 Instance ID
    Value: !Ref MyEC2Instance

  S3BucketName:
    Description: S3 Bucket Name
    Value: !Ref MyS3Bucket

```

### CloudFormation Template Reference

 [AWS CloudFormation Template Guide](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/template-guide.html)
 >  Use this reference to explore more advanced topics and real-world use cases.
