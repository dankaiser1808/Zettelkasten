#aws 

The KMS keys can be divided into different types based on the use case of the key:

- Customer Master Keys
	- primary resource used for decryption, encryption and re-encryption
- Data Key
	- to encrypt and decrypt large amount of data
- Imported Key Material
	- Self provided key added to AWS KMS
- AWS Managed Keys
	- Automatic created keys used and managed by AWS, for our used Services like S3, EBS, SQS.
- AWS Owned Keys
	- Internally used by AWS across multiple Accounts, not visible to us