# awscli

### List public IP addresses

```
aws ec2 describe-instances --region us-west-2 --max-items 999 | grep PublicIpAddress | awk '{print $2}' | sed -E 's/"|,//g'
```
