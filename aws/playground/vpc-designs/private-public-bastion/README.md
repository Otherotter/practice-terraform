# Chart

![aws diagram](https://github.com/Otherotter/practice-terraform/blob/main/aws/playground/vpc-designs/private-public-bastion/VPC-Public-Private-Bastion.png)

# Description
This setup creates a public bastion, private bastion, and subservent machines serving the private bastion.

Both public bastion and private bastion have the same ssh key allowing login. The ssh key should be found in your local machine. You can log into the private bastion with the following command.
```python
ssh -J <PUBLIC_BASTION_IPADDRESS> <PRIVATE_BASTION_IPADDRESS>
```

The private bastion is the master machine to the subservent machines. Each subservent machine has a ssh key allowing the private bastion to ssh login into each of them. The key must be create in your machine, then it must be transfered after the terrraform script has ran. Use the following command to secure copy it the private bastion.
```python
scp -j <PUBLIC_BASTION_IPADDRESS> ./key/private-bastion <PRIVATE_BASTION_IPADDRESS>:~/.ssh
```

Once the private key has be copied into the private bastion, you can ssh into each subservent machine using.
```python
ssh -i ~/.ssh/private-bastion <SUBSERVENTS_IPADDRESS>
```



