# Sample repo - Kitchen-Terraform with "groups" verifier

## Requirments

Make sure you have the following prerequisites for this tutorial  
  
An AWS Account  
An AWS Access Key ID  
An AWS Secret Key  
An AWS Keypair  
Terraform installed  
Bundler installed  
Ruby 2.3.1  
The default security group on your account must allow SSH access from your IP address

### How to use it:
-   Clone the repo.
```
git clone https://github.com/chavo1/kitchen-terraform-ec2.git
```

- Add a needed data into the "testing.tfvars" file.

```
access_key = ""
secret_key = ""
key_name = ""
region = ""
ami = ""
instance_type = ""
```

- Download needed gems.
```
$ bundle install
```
- We are ready to start kitchen.
```
$ bundle exec kitchen converge
$ bundle exec kitchen verify
```
-   the result from the test should be as follow:
```
$$$$$$ Terraform v0.11.10 is supported
-----> Setting up <default-ubuntu>...
       Finished setting up <default-ubuntu> (0m0.00s).
-----> Verifying <default-ubuntu>...
       Verifying host 'ec2-34-207-195-209.compute-1.amazonaws.com' of group 'remote'
       Loaded default

Profile: default
Version: (not specified)
Target:  ssh://ubuntu@ec2-34-207-195-209.compute-1.amazonaws.com:22

  ✔  operating_system: Command: `lsb_release -a`
     ✔  Command: `lsb_release -a` stdout should match /Ubuntu/


Profile Summary: 1 successful control, 0 control failures, 0 controls skipped
Test Summary: 1 successful, 0 failures, 0 skipped
       Finished verifying <default-ubuntu> (0m6.18s).
-----> Kitchen is finished. (0m8.52s)
```
- Do not forget to destroy EC2 instance
```
$ bundle exec kitchen destroy
```
