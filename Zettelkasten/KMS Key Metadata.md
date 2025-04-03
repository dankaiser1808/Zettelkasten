#aws 

A KMS key contains the following metadata to provide us with useful information about the key itself.

- ARN
	- unique identifier of the key
- Key Material
	-  the portion of the key for the actual encryption and decryption
- State
	- Disabled, enabled, pending, deletion or import
- Policies
	- indicates who can use the key and what operations can be performed with it
- Key Usage
	- Specifies the cryptographic operation itself, for symmetric and asymmetric keys
- Key Spec
	- configurations for the key like algorithm size
- Key Origin
	- Either from AWS, externally, or AWS_CLOUDHSM
- RotationStatus
- Alias
- Tags
- CreationDate

---
[[Resource Metadata ARN]]
[[Metadata]]
[[Symmetric Encryption]]
[[Asymmetric Encryption]]