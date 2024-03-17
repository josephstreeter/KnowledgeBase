# SSH Connect

## Authenticate with a Specific Key
A specific key can be specified in the SSH command. 
```
ssh -i ~/.ssh/id_rsa_host username@host.domain.com
```
## Compare Public Key Fingerprint
If you are having trouble logging into a host or a service you can confirm that the fingerprint of your public key matches what was uploaded.
```
ssh-keygen -l -E md5 -f ~/.ssh/id_rsa_ado.pub
```
## Test Authentication
The following command will test authentiction to a specific host. 
```
ssh -T git@ssh.dev.azure.com
```
In the case of source control services, you may get the following error. This is simply because the service is not intended for shell access and is completely normal. 
```
remote: Shell access is not supported.
```
