# YES3 Scanner: Yet Another S3 Scanner

YES3 scans an AWS Account for potential S3 security issues in the following categories:

* Access Issues such as Public Access
* Preventative S3 Security Settings
* Additional Security such as Encryption
* Ransomware Protection, Data Protection, and Recovery

For help or feedback, contact us at [info@fogsecurity.io](mailto:info@fogsecurity.io).  We are continuing to build in this space and are developing a more comprehensive scanner with multi-account (Organization) and object-level scanning.  If you're interested in joining a private beta, reach out to us.

Blog Post: <>

## Checks

YES3 Scanner checks for the following S3 configuration items:

### Access Issues and Public Access
- Bucket Access Control Lists (ACLs)
- Bucket Policy (Resource-Based Policy)
- Bucket Website Settings

#### Preventative S3 Security Settings
- Account Public Access Block
- Bucket Public Access Block
- Disabled ACLs (via Ownership Controls)

#### Additional Security
- Bucket Encryption Settings

#### Ransomware Protection & Recovery
- Object Lock Configuration
- Bucket Versioning Settings
- Bucket Lifecycle Configuration

## Running YES3 Scanner

```
python3 yes3.py --profile <your_profile_here> --region <region_specifier>
```

Note: While S3 is global, YES3 will check Service Quotas for bucket limits and thus will need a region specified for the BOTO3 client.  It will check S3 globally (assuming proper permissions) as well as the account (global) limit for buckets.

Example output:

```
YES3 SCANNER RESULTS
----------------------------
AWS Account: 123412341234
Account Settings
Account Block Public Access Overall Status: OK
----------------------------
Bucket Summary
Total Buckets: 14
----------------------------
Buckets potentially public: 0
[]
----------------------------
Buckets with Access Issues: 1
sample-locked-bucket
----------------------------
Buckets with default S3-Owned Encryption: 6
Buckets with a Block Public Access setting disabled: 3
Buckets with Bucket ACLs Enabled: 2
Buckets with ACLs set to public: 0
Buckets with Bucket Policy set to public: 1
Buckets with Object Lock disabled: 5
Buckets with Versioning disabled: 4
Buckets with Lifecycle Config Set to Expiration: 1
Buckets with Public Access from Website Setting: 0
----------------------------
Additional Bucket Details
Buckets with default S3-Owned Encryption: sample-bucket-1, sample-bucket-2, sample-bucket-3, sample-bucket-4, sample-bucket-5, sample-bucket-6

Buckets with a Block Public Access setting disabled: sample-bucket-1, sample-bucket-2, sample-bucket-3

Buckets with Bucket ACLs Enabled: sample-bucket-1, sample-bucket-2

Buckets with ACLs set to public: 

Buckets with Bucket Policy set to public: sample-bucket-1

Buckets with Object Lock disabled: sample-bucket-1, sample-bucket-2, sample-bucket-3, sample-bucket-4, sample-bucket-5

Buckets with Versioning disabled: sample-bucket-1, sample-bucket-2, sample-bucket-3, sample-bucket-4

Buckets with Lifecycle Config Set to Expiration: sample-bucket-7

Buckets with Public Access from Website Setting: 

``` 

## Installing YES3 Scanner and Requirements

- Python 3 and AWS's boto3 library are required.
- AWS credentials and appropriate access are needed to run YES3.  For more information about IAM Requirements for this tool, see our [IAM documentation](iam/iam.md) which details how to install IAM for YES3 and required IAM permissions.

Requirements can be installed via pip3 install and the requirements.txt file. A python virtual environment can be used if desired.

```
pip3 install -r requirements.txt
```

For information on configuring your AWS Credentials, see AWS's documentation [here](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-quickstart.html)

## Contact

Contact us at info@fogsecurity.io for support and more information.
