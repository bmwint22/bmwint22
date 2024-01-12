Benita Mwintshi...Wecloud Project1
aws ec2 create-vpc \
    --cidr-block 10.0.0.0/16 \
    --tag-specification "ResourceType=vpc,Tags=[{Key=project,Value=wecloud}]" \
    > create-vpc-output.json

 aws ec2 create-subnet \
    --vpc-id vpc-01536b0a1c121ea75 \
    --cidr-block 10.0.0.0/24 \
    --tag-specifications "ResourceType=subnet,Tags=[{Key=project,Value=wecloud-cli-public-subnet}]" \
    > create-public-subnet-output.json 

aws ec2 create-internet-gateway \
    --tag-specifications "ResourceType=internet-gateway,Tags=[{Key=project,Value=wecloud-igw}]" \
    > create-internet-gateway-output.json

aws ec2 attach-internet-gateway \
    --internet-gateway-id igw-0440d0cc5d6890571 \
    --vpc-id vpc-01536b0a1c121ea75


aws ec2 create-route-table --vpc-id vpc-01536b0a1c121ea75 \
 --tag-specifications "ResourceType=route-table,Tags=[{Key=project,Value=wecloud-cli-public-route-table}]" \
    > create-public-route-table-output.json 

 aws ec2 associate-route-table --route-table-id rtb-08e1325ec3cf35cd7 --subnet-id subnet-09338ccc56286cbfb   

 aws ec2 create-route --route-table-id rtb-08e1325ec3cf35cd7 --destination-cidr-block 0.0.0.0/0 --gateway-id igw-0440d0cc5d6890571

"Vpc": {
        "CidrBlock": "10.0.0.0/16",
        "DhcpOptionsId": "dopt-02fec609317ccb291",
        "State": "pending",
        "VpcId": "vpc-01536b0a1c121ea75",
        "OwnerId": "181022609185",
        "InstanceTenancy": "default",
        "Ipv6CidrBlockAssociationSet": [],
        "CidrBlockAssociationSet": [
            {
                "AssociationId": "vpc-cidr-assoc-0abca4c36060b7474",
                "CidrBlock": "10.0.0.0/16",
                "CidrBlockState": {
                    "State": "associated"
                }
            }
        ],
        "IsDefault": false,
        "Tags": [
            {
                "Key": "project",
                "Value": "wecloud"
            }
        ]
    }
}
"Subnet": {
        "AvailabilityZone": "us-east-1b",
        "AvailabilityZoneId": "use1-az4",
        "AvailableIpAddressCount": 251,
        "CidrBlock": "10.0.0.0/24",
        "DefaultForAz": false,
        "MapPublicIpOnLaunch": false,
        "State": "available",
        "SubnetId": "subnet-09338ccc56286cbfb",
        "VpcId": "vpc-01536b0a1c121ea75",
        "OwnerId": "181022609185",
        "AssignIpv6AddressOnCreation": false,
        "Ipv6CidrBlockAssociationSet": [],
        "Tags": [
            {
                "Key": "project",
                "Value": "wecloud-cli-public-subnet"
            }
        ],
        "SubnetArn": "arn:aws:ec2:us-east-1:181022609185:subnet/subnet-09338ccc56286cbfb",
        "EnableDns64": false,
        "Ipv6Native": false,
        "PrivateDnsNameOptionsOnLaunch": {
            "HostnameType": "ip-name",
            "EnableResourceNameDnsARecord": false,
            "EnableResourceNameDnsAAAARecord": false
        }
    }
}
 "RouteTable": {
        "Associations": [],
        "PropagatingVgws": [],
        "RouteTableId": "rtb-08e1325ec3cf35cd7",
        "Routes": [
            {
                "DestinationCidrBlock": "10.0.0.0/16",
                "GatewayId": "local",
                "Origin": "CreateRouteTable",
                "State": "active"
            }
        ],
        "Tags": [
            {
                "Key": "project",
                "Value": "wecloud-cli-public-route-table"
            }
        ],
        "VpcId": "vpc-01536b0a1c121ea75",
        "OwnerId": "181022609185"
    }
}
{
    "InternetGateway": {
        "Attachments": [],
        "InternetGatewayId": "igw-0440d0cc5d6890571",
        "OwnerId": "181022609185",
        "Tags": [
            {
                "Key": "project",
                "Value": "wecloud-igw"
            }
        ]
    }
}
Host 52.23.225.41
  HostName 52.23.225.41
  IdentityFile ~/.ssh/benita_rsa.pub.pem
  User ubuntu

Host 54.145.56.95
  HostName 54.145.56.95
  IdentityFile ~/.ssh/benita_rsa.pub.pem
  User ubuntu

Host 54.82.169.194
  HostName 54.82.169.194
  IdentityFile ~/.ssh/benita_rsa.pub.pem
  User ubuntu

Host ubuntu
  HostName ubuntu
  IdentityFile ~/.ssh/benita.pem

Host 192.168.64.5
  HostName 192.168.64.5
  User ubuntu
