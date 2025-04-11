#consume 

https://docs.aws.amazon.com/cli/latest/reference/kms/encrypt.html
https://docs.aws.amazon.com/cli/latest/reference/kms/decrypt.html

aws kms encrypt --key-id 6f504b98-d4ca-491e-8923-87f55fb4a929 --plaintext fileb://SensitiveData.txt --output text --query CiphertextBlob | base64 --decode > EncryptedData.**bin**


aws kms decrypt \
    --ciphertext-blob fileb://ExampleEncryptedFile \
    --key-id 0987dcba-09fe-87dc-65ba-ab0987654321 \
    --output text \
    --query Plaintext | base64 \
    --decode > ExamplePlaintextFile

