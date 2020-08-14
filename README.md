# Kubernetes @ Elastic Kubernetes Service (Amazon EKS)

```console
$ eks-cluster --help ;

Use:  eks-cluster
      --access-pubkey='kubernetes.pub'
      --capacity='1.2.3'
      --cluster-name='emvaldes'
      --cluster-version='1.15'
      --delete-cluster
      --create-cluster
      --deploy-cluster
      --deploy-dashboard
      --deploy-prometheus
      --deploy-prototype
      --describe-cluster
      --enable-autoscaling
      --enable-cloudwatch
      --enable-fargate
      --enable-metrics
      --help-create
      --help-delete
      --interactive
      --kubeconfig='/Users/emvaldes/.kube/config'
      --nodegroup-name='prototype'
      --profile='default'
      --region='us-east-1'
      --scale-cluster='0'
      --target-cluster='emvaldes.prototype'
      --team-creator='DevOps Team'
      --team-member='Eduardo Valdes'
      --team-owner='Infrastructure'
      --zones='us-east-1a,us-east-1b,us-east-1c'
      --verbose

Goodbye!
```

```console
time {
    bash -x eks-cluster \
    --create-cluster=prototype.devops \
    --region=us-west-2 \
    --zones="us-west-2a,us-west-2b,us-west-2c" \
    --verbose \
    --debug;
  };
```

```console
$ eksctl create cluster \
  --alb-ingress-access \
  --appmesh-access \
  --asg-access \
  --auto-kubeconfig \
  --fargate \
  --full-ecr-access \
  --managed \
  --name prototype \
  --nodegroup-name devops \
  --nodes-max 3 \
  --nodes-min 2 \
  --profile default \
  --region us-west-2 \
  --ssh-access \
  --ssh-public-key /Users/emvaldes/.ssh/kubernetes.pub \
  --tags 'Owner=Infrastructure,Team=DevOps Team,Creator=Eduardo Valdes' \
  --timeout 60m0s \
  --verbose 5 \
  --version 1.15 \
  --zones us-west-2a,us-west-2b,us-west-2c \
;
```

```console
2020-08-13T13:31:31-07:00 [ℹ]  eksctl version 0.25.0
2020-08-13T13:31:31-07:00 [ℹ]  using region us-west-2
2020-08-13T13:31:31-07:00 [▶]  DEBUG: Request sts/GetCallerIdentity Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: sts.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 43
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/sts/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=4fe0df46753f303aac6f84362fbf46e6a7881da4b34ae32db7cf7a9e93008fa6
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T203131Z
Accept-Encoding: gzip
-----------------------------------------------------
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Content-Length: 411
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:31:31 GMT
X-Amzn-Requestid: ec50e120-c591-4731-834b-efd0856b5b9d
-----------------------------------------------------
```

```xml
<GetCallerIdentityResponse xmlns="https://sts.amazonaws.com/doc/2011-06-15/">
  <GetCallerIdentityResult>
    <Arn>arn:aws:iam::738054984624:user/eduardo.valdes</Arn>
    <UserId>AIDAJ465PRJTNHYBY4JVY</UserId>
    <Account>738054984624</Account>
  </GetCallerIdentityResult>
  <ResponseMetadata>
    <RequestId>ec50e120-c591-4731-834b-efd0856b5b9d</RequestId>
  </ResponseMetadata>
</GetCallerIdentityResponse>
```

```console
2020-08-13T13:31:32-07:00 [▶]  role ARN for the current session is "arn:aws:iam::738054984624:user/eduardo.valdes"
2020-08-13T13:31:32-07:00 [▶]  VPC CIDR (192.168.0.0/16) was divided into 8 subnets [192.168.0.0/19 192.168.32.0/19 192.168.64.0/19 192.168.96.0/19 192.168.128.0/19 192.168.160.0/19 192.168.192.0/19 192.168.224.0/19]
2020-08-13T13:31:32-07:00 [ℹ]  subnets for us-west-2a - public:192.168.0.0/19 private:192.168.96.0/19
2020-08-13T13:31:32-07:00 [ℹ]  subnets for us-west-2b - public:192.168.32.0/19 private:192.168.128.0/19
2020-08-13T13:31:32-07:00 [ℹ]  subnets for us-west-2c - public:192.168.64.0/19 private:192.168.160.0/19
2020-08-13T13:31:32-07:00 [ℹ]  using SSH public key "/Users/emvaldes/.ssh/kubernetes.pub" as "eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0"
2020-08-13T13:31:32-07:00 [▶]  DEBUG: Request ec2/DescribeKeyPairs Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 162
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=e1cfcf89212b14da4f6d57443e7f479e8c07c43ce1e8e5258f06105346342d74
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T203132Z
Accept-Encoding: gzip
-----------------------------------------------------
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 400 Bad Request
Connection: close
Transfer-Encoding: chunked
Date: Thu, 13 Aug 2020 20:31:32 GMT
Server: AmazonEC2
-----------------------------------------------------
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Response><Errors><Error><Code>InvalidKeyPair.NotFound</Code><Message>The key pair 'eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0' does not exist</Message></Error></Errors><RequestID>9d17baf4-d91b-44aa-acbf-63394899cac3</RequestID></Response>
```

```console
2020-08-13T13:31:32-07:00 [▶]  DEBUG: Validate Response ec2/DescribeKeyPairs failed, attempt 0/13, error InvalidKeyPair.NotFound: The key pair 'eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0' does not exist
	status code: 400, request id: 9d17baf4-d91b-44aa-acbf-63394899cac3
2020-08-13T13:31:32-07:00 [▶]  importing SSH public key "eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0"
2020-08-13T13:31:32-07:00 [▶]  DEBUG: Request ec2/ImportKeyPair Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 1192
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=efaa2adaa63c96445b82b220c8ef15c0bf903dae1d6027bf8091077162a50063
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T203132Z
Accept-Encoding: gzip
-----------------------------------------------------
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Content-Length: 438
Content-Type: text/xml;charset=UTF-8
Date: Thu, 13 Aug 2020 20:31:32 GMT
Server: AmazonEC2
X-Amzn-Requestid: f23d980f-07e4-4367-83a4-d6fa70c6ae43
-----------------------------------------------------
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ImportKeyPairResponse xmlns="http://ec2.amazonaws.com/doc/2016-11-15/">
    <requestId>f23d980f-07e4-4367-83a4-d6fa70c6ae43</requestId>
    <keyName>eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0</keyName>
    <keyPairId>key-08a595cf495114768</keyPairId>
    <keyFingerprint>86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0</keyFingerprint>
</ImportKeyPairResponse>
```

```console
2020-08-13T13:31:33-07:00 [ℹ]  using Kubernetes version 1.15
2020-08-13T13:31:33-07:00 [ℹ]  creating EKS cluster "prototype" in "us-west-2" region with Fargate profile and managed nodes
2020-08-13T13:31:33-07:00 [▶]  cfg.json = \
```

```json
{
    "kind": "ClusterConfig",
    "apiVersion": "eksctl.io/v1alpha5",
    "metadata": {
        "name": "prototype",
        "region": "us-west-2",
        "version": "1.15",
        "tags": {
            "Creator": "Eduardo Valdes",
            "Owner": "Infrastructure",
            "Team": "DevOps Team"
        }
    },
    "iam": {
        "withOIDC": false
    },
    "vpc": {
        "cidr": "192.168.0.0/16",
        "subnets": {
            "private": {
                "us-west-2a": {
                    "cidr": "192.168.96.0/19"
                },
                "us-west-2b": {
                    "cidr": "192.168.128.0/19"
                },
                "us-west-2c": {
                    "cidr": "192.168.160.0/19"
                }
            },
            "public": {
                "us-west-2a": {
                    "cidr": "192.168.0.0/19"
                },
                "us-west-2b": {
                    "cidr": "192.168.32.0/19"
                },
                "us-west-2c": {
                    "cidr": "192.168.64.0/19"
                }
            }
        },
        "autoAllocateIPv6": false,
        "nat": {
            "gateway": "Single"
        },
        "clusterEndpoints": {
            "privateAccess": false,
            "publicAccess": true
        }
    },
    "privateCluster": {
        "enabled": false
    },
    "managedNodeGroups": [
        {
            "name": "devops",
            "amiFamily": "AmazonLinux2",
            "instanceType": "m5.large",
            "desiredCapacity": 2,
            "minSize": 2,
            "maxSize": 3,
            "volumeSize": 80,
            "ssh": {
                "allow": true,
                "publicKeyPath": "/Users/emvaldes/.ssh/kubernetes.pub",
                "publicKeyName": "eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0"
            },
            "labels": {
                "alpha.eksctl.io/cluster-name": "prototype",
                "alpha.eksctl.io/nodegroup-name": "devops"
            },
            "privateNetworking": false,
            "tags": {
                "alpha.eksctl.io/nodegroup-name": "devops",
                "alpha.eksctl.io/nodegroup-type": "managed"
            },
            "iam": {
                "withAddonPolicies": {
                    "imageBuilder": true,
                    "autoScaler": true,
                    "externalDNS": false,
                    "certManager": false,
                    "appMesh": true,
                    "appMeshPreview": false,
                    "ebs": false,
                    "fsx": false,
                    "efs": false,
                    "albIngress": true,
                    "xRay": false,
                    "cloudWatch": false
                }
            }
        }
    ],
    "fargateProfiles": [
        {
            "name": "fp-default",
            "selectors": [
                {
                    "namespace": "default"
                },
                {
                    "namespace": "kube-system"
                }
            ]
        }
    ],
    "availabilityZones": [
        "us-west-2a",
        "us-west-2b",
        "us-west-2c"
    ],
    "cloudWatch": {
        "clusterLogging": {}
    }
}
```

```console
2020-08-13T13:31:33-07:00 [ℹ]  will create 2 separate CloudFormation stacks for cluster itself and the initial managed nodegroup
2020-08-13T13:31:33-07:00 [ℹ]  if you encounter any issues, check CloudFormation console or try 'eksctl utils describe-stacks --region=us-west-2 --cluster=prototype'
2020-08-13T13:31:33-07:00 [ℹ]  CloudWatch logging will not be enabled for cluster "prototype" in "us-west-2"
2020-08-13T13:31:33-07:00 [ℹ]  you can enable it with 'eksctl utils update-cluster-logging --region=us-west-2 --cluster=prototype'
2020-08-13T13:31:33-07:00 [ℹ]  Kubernetes API endpoint access will use default of {publicAccess=true, privateAccess=false} for cluster "prototype" in "us-west-2"
2020-08-13T13:31:33-07:00 [ℹ]  2 sequential tasks: { create cluster control plane "prototype", 2 sequential sub-tasks: { 2 sequential sub-tasks: { tag cluster, create fargate profiles }, create managed nodegroup "devops" } }
2020-08-13T13:31:33-07:00 [▶]  started task: create cluster control plane "prototype"
2020-08-13T13:31:33-07:00 [ℹ]  building cluster stack "eksctl-prototype-cluster"
2020-08-13T13:31:33-07:00 [▶]  CreateStackInput =
```

```json
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "EKS cluster (dedicated VPC: true, dedicated IAM: true) [created and managed by eksctl]",
  "Mappings": {
    "ServicePrincipalPartitionMap": {
      "aws": {
        "EC2": "ec2.amazonaws.com",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      },
      "aws-cn": {
        "EC2": "ec2.amazonaws.com.cn",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      },
      "aws-us-gov": {
        "EC2": "ec2.amazonaws.com",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      }
    }
  },
  "Resources": {
    "ClusterSharedNodeSecurityGroup": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Communication between all nodes in the cluster",
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/ClusterSharedNodeSecurityGroup"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "ControlPlane": {
      "Type": "AWS::EKS::Cluster",
      "Properties": {
        "Name": "prototype",
        "ResourcesVpcConfig": {
          "SecurityGroupIds": [
            {
              "Ref": "ControlPlaneSecurityGroup"
            }
          ],
          "SubnetIds": [
            {
              "Ref": "SubnetPublicUSWEST2B"
            },
            {
              "Ref": "SubnetPublicUSWEST2C"
            },
            {
              "Ref": "SubnetPublicUSWEST2A"
            },
            {
              "Ref": "SubnetPrivateUSWEST2A"
            },
            {
              "Ref": "SubnetPrivateUSWEST2B"
            },
            {
              "Ref": "SubnetPrivateUSWEST2C"
            }
          ]
        },
        "RoleArn": {
          "Fn::GetAtt": [
            "ServiceRole",
            "Arn"
          ]
        },
        "Version": "1.15"
      }
    },
    "ControlPlaneSecurityGroup": {
      "Type": "AWS::EC2::SecurityGroup",
      "Properties": {
        "GroupDescription": "Communication between the control plane and worker nodegroups",
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/ControlPlaneSecurityGroup"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "FargatePodExecutionRole": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": [
                "sts:AssumeRole"
              ],
              "Effect": "Allow",
              "Principal": {
                "Service": [
                  {
                    "Fn::FindInMap": [
                      "ServicePrincipalPartitionMap",
                      {
                        "Ref": "AWS::Partition"
                      },
                      "EKS"
                    ]
                  },
                  {
                    "Fn::FindInMap": [
                      "ServicePrincipalPartitionMap",
                      {
                        "Ref": "AWS::Partition"
                      },
                      "EKSFargatePods"
                    ]
                  }
                ]
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "ManagedPolicyArns": [
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEKSFargatePodExecutionRolePolicy"
          }
        ],
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/FargatePodExecutionRole"
            }
          }
        ]
      }
    },
    "IngressDefaultClusterToNodeSG": {
      "Type": "AWS::EC2::SecurityGroupIngress",
      "Properties": {
        "Description": "Allow managed and unmanaged nodes to communicate with each other (all ports)",
        "FromPort": 0,
        "GroupId": {
          "Ref": "ClusterSharedNodeSecurityGroup"
        },
        "IpProtocol": "-1",
        "SourceSecurityGroupId": {
          "Fn::GetAtt": [
            "ControlPlane",
            "ClusterSecurityGroupId"
          ]
        },
        "ToPort": 65535
      }
    },
    "IngressInterNodeGroupSG": {
      "Type": "AWS::EC2::SecurityGroupIngress",
      "Properties": {
        "Description": "Allow nodes to communicate with each other (all ports)",
        "FromPort": 0,
        "GroupId": {
          "Ref": "ClusterSharedNodeSecurityGroup"
        },
        "IpProtocol": "-1",
        "SourceSecurityGroupId": {
          "Ref": "ClusterSharedNodeSecurityGroup"
        },
        "ToPort": 65535
      }
    },
    "IngressNodeToDefaultClusterSG": {
      "Type": "AWS::EC2::SecurityGroupIngress",
      "Properties": {
        "Description": "Allow unmanaged nodes to communicate with control plane (all ports)",
        "FromPort": 0,
        "GroupId": {
          "Fn::GetAtt": [
            "ControlPlane",
            "ClusterSecurityGroupId"
          ]
        },
        "IpProtocol": "-1",
        "SourceSecurityGroupId": {
          "Ref": "ClusterSharedNodeSecurityGroup"
        },
        "ToPort": 65535
      }
    },
    "InternetGateway": {
      "Type": "AWS::EC2::InternetGateway",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/InternetGateway"
            }
          }
        ]
      }
    },
    "NATGateway": {
      "Type": "AWS::EC2::NatGateway",
      "Properties": {
        "AllocationId": {
          "Fn::GetAtt": [
            "NATIP",
            "AllocationId"
          ]
        },
        "SubnetId": {
          "Ref": "SubnetPublicUSWEST2A"
        },
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/NATGateway"
            }
          }
        ]
      }
    },
    "NATIP": {
      "Type": "AWS::EC2::EIP",
      "Properties": {
        "Domain": "vpc",
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/NATIP"
            }
          }
        ]
      }
    },
    "NATPrivateSubnetRouteUSWEST2A": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "DestinationCidrBlock": "0.0.0.0/0",
        "NatGatewayId": {
          "Ref": "NATGateway"
        },
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2A"
        }
      }
    },
    "NATPrivateSubnetRouteUSWEST2B": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "DestinationCidrBlock": "0.0.0.0/0",
        "NatGatewayId": {
          "Ref": "NATGateway"
        },
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2B"
        }
      }
    },
    "NATPrivateSubnetRouteUSWEST2C": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "DestinationCidrBlock": "0.0.0.0/0",
        "NatGatewayId": {
          "Ref": "NATGateway"
        },
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2C"
        }
      }
    },
    "PolicyCloudWatchMetrics": {
      "Type": "AWS::IAM::Policy",
      "Properties": {
        "PolicyDocument": {
          "Statement": [
            {
              "Action": [
                "cloudwatch:PutMetricData"
              ],
              "Effect": "Allow",
              "Resource": "*"
            }
          ],
          "Version": "2012-10-17"
        },
        "PolicyName": {
          "Fn::Sub": "${AWS::StackName}-PolicyCloudWatchMetrics"
        },
        "Roles": [
          {
            "Ref": "ServiceRole"
          }
        ]
      }
    },
    "PolicyELBPermissions": {
      "Type": "AWS::IAM::Policy",
      "Properties": {
        "PolicyDocument": {
          "Statement": [
            {
              "Action": [
                "ec2:DescribeAccountAttributes"
              ],
              "Effect": "Allow",
              "Resource": "*"
            }
          ],
          "Version": "2012-10-17"
        },
        "PolicyName": {
          "Fn::Sub": "${AWS::StackName}-PolicyELBPermissions"
        },
        "Roles": [
          {
            "Ref": "ServiceRole"
          }
        ]
      }
    },
    "PrivateRouteTableUSWEST2A": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/PrivateRouteTableUSWEST2A"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "PrivateRouteTableUSWEST2B": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/PrivateRouteTableUSWEST2B"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "PrivateRouteTableUSWEST2C": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/PrivateRouteTableUSWEST2C"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "PublicRouteTable": {
      "Type": "AWS::EC2::RouteTable",
      "Properties": {
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/PublicRouteTable"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "PublicSubnetRoute": {
      "Type": "AWS::EC2::Route",
      "Properties": {
        "DestinationCidrBlock": "0.0.0.0/0",
        "GatewayId": {
          "Ref": "InternetGateway"
        },
        "RouteTableId": {
          "Ref": "PublicRouteTable"
        }
      },
      "DependsOn": [
        "VPCGatewayAttachment"
      ]
    },
    "RouteTableAssociationPrivateUSWEST2A": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2A"
        },
        "SubnetId": {
          "Ref": "SubnetPrivateUSWEST2A"
        }
      }
    },
    "RouteTableAssociationPrivateUSWEST2B": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2B"
        },
        "SubnetId": {
          "Ref": "SubnetPrivateUSWEST2B"
        }
      }
    },
    "RouteTableAssociationPrivateUSWEST2C": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PrivateRouteTableUSWEST2C"
        },
        "SubnetId": {
          "Ref": "SubnetPrivateUSWEST2C"
        }
      }
    },
    "RouteTableAssociationPublicUSWEST2A": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PublicRouteTable"
        },
        "SubnetId": {
          "Ref": "SubnetPublicUSWEST2A"
        }
      }
    },
    "RouteTableAssociationPublicUSWEST2B": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PublicRouteTable"
        },
        "SubnetId": {
          "Ref": "SubnetPublicUSWEST2B"
        }
      }
    },
    "RouteTableAssociationPublicUSWEST2C": {
      "Type": "AWS::EC2::SubnetRouteTableAssociation",
      "Properties": {
        "RouteTableId": {
          "Ref": "PublicRouteTable"
        },
        "SubnetId": {
          "Ref": "SubnetPublicUSWEST2C"
        }
      }
    },
    "ServiceRole": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": [
                "sts:AssumeRole"
              ],
              "Effect": "Allow",
              "Principal": {
                "Service": [
                  {
                    "Fn::FindInMap": [
                      "ServicePrincipalPartitionMap",
                      {
                        "Ref": "AWS::Partition"
                      },
                      "EKS"
                    ]
                  },
                  {
                    "Fn::FindInMap": [
                      "ServicePrincipalPartitionMap",
                      {
                        "Ref": "AWS::Partition"
                      },
                      "EKSFargatePods"
                    ]
                  }
                ]
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "ManagedPolicyArns": [
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEKSClusterPolicy"
          }
        ],
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/ServiceRole"
            }
          }
        ]
      }
    },
    "SubnetPrivateUSWEST2A": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2a",
        "CidrBlock": "192.168.96.0/19",
        "Tags": [
          {
            "Key": "kubernetes.io/role/internal-elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPrivateUSWEST2A"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "SubnetPrivateUSWEST2B": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2b",
        "CidrBlock": "192.168.128.0/19",
        "Tags": [
          {
            "Key": "kubernetes.io/role/internal-elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPrivateUSWEST2B"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "SubnetPrivateUSWEST2C": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2c",
        "CidrBlock": "192.168.160.0/19",
        "Tags": [
          {
            "Key": "kubernetes.io/role/internal-elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPrivateUSWEST2C"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "SubnetPublicUSWEST2A": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2a",
        "CidrBlock": "192.168.0.0/19",
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "kubernetes.io/role/elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPublicUSWEST2A"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "SubnetPublicUSWEST2B": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2b",
        "CidrBlock": "192.168.32.0/19",
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "kubernetes.io/role/elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPublicUSWEST2B"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "SubnetPublicUSWEST2C": {
      "Type": "AWS::EC2::Subnet",
      "Properties": {
        "AvailabilityZone": "us-west-2c",
        "CidrBlock": "192.168.64.0/19",
        "MapPublicIpOnLaunch": true,
        "Tags": [
          {
            "Key": "kubernetes.io/role/elb",
            "Value": "1"
          },
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/SubnetPublicUSWEST2C"
            }
          }
        ],
        "VpcId": {
          "Ref": "VPC"
        }
      }
    },
    "VPC": {
      "Type": "AWS::EC2::VPC",
      "Properties": {
        "CidrBlock": "192.168.0.0/16",
        "EnableDnsHostnames": true,
        "EnableDnsSupport": true,
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/VPC"
            }
          }
        ]
      }
    },
    "VPCGatewayAttachment": {
      "Type": "AWS::EC2::VPCGatewayAttachment",
      "Properties": {
        "InternetGatewayId": {
          "Ref": "InternetGateway"
        },
        "VpcId": {
          "Ref": "VPC"
        }
      }
    }
  },
  "Outputs": {
    "ARN": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::ARN"
        }
      },
      "Value": {
        "Fn::GetAtt": [
          "ControlPlane",
          "Arn"
        ]
      }
    },
    "CertificateAuthorityData": {
      "Value": {
        "Fn::GetAtt": [
          "ControlPlane",
          "CertificateAuthorityData"
        ]
      }
    },
    "ClusterSecurityGroupId": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::ClusterSecurityGroupId"
        }
      },
      "Value": {
        "Fn::GetAtt": [
          "ControlPlane",
          "ClusterSecurityGroupId"
        ]
      }
    },
    "ClusterStackName": {
      "Value": {
        "Ref": "AWS::StackName"
      }
    },
    "Endpoint": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::Endpoint"
        }
      },
      "Value": {
        "Fn::GetAtt": [
          "ControlPlane",
          "Endpoint"
        ]
      }
    },
    "FargatePodExecutionRoleARN": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::FargatePodExecutionRoleARN"
        }
      },
      "Value": {
        "Fn::GetAtt": [
          "FargatePodExecutionRole",
          "Arn"
        ]
      }
    },
    "FeatureNATMode": {
      "Value": "Single"
    },
    "SecurityGroup": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::SecurityGroup"
        }
      },
      "Value": {
        "Ref": "ControlPlaneSecurityGroup"
      }
    },
    "ServiceRoleARN": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::ServiceRoleARN"
        }
      },
      "Value": {
        "Fn::GetAtt": [
          "ServiceRole",
          "Arn"
        ]
      }
    },
    "SharedNodeSecurityGroup": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::SharedNodeSecurityGroup"
        }
      },
      "Value": {
        "Ref": "ClusterSharedNodeSecurityGroup"
      }
    },
    "SubnetsPrivate": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::SubnetsPrivate"
        }
      },
      "Value": {
        "Fn::Join": [
          ",",
          [
            {
              "Ref": "SubnetPrivateUSWEST2A"
            },
            {
              "Ref": "SubnetPrivateUSWEST2B"
            },
            {
              "Ref": "SubnetPrivateUSWEST2C"
            }
          ]
        ]
      }
    },
    "SubnetsPublic": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::SubnetsPublic"
        }
      },
      "Value": {
        "Fn::Join": [
          ",",
          [
            {
              "Ref": "SubnetPublicUSWEST2B"
            },
            {
              "Ref": "SubnetPublicUSWEST2C"
            },
            {
              "Ref": "SubnetPublicUSWEST2A"
            }
          ]
        ]
      }
    },
    "VPC": {
      "Export": {
        "Name": {
          "Fn::Sub": "${AWS::StackName}::VPC"
        }
      },
      "Value": {
        "Ref": "VPC"
      }
    }
  }
}
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 28903
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=4bc5de3cd2b5261ec77fe8919a6c5cbfe2fb8cbb74eba9783a0fe26fad8f52f0
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T203133Z
Accept-Encoding: gzip
-----------------------------------------------------
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Content-Length: 392
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:31:33 GMT
X-Amzn-Requestid: ce56b3e8-bb82-4115-8e77-278960bd50ab
-----------------------------------------------------
```

```xml
<CreateStackResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <CreateStackResult>
    <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</StackId>
  </CreateStackResult>
  <ResponseMetadata>
    <RequestId>ce56b3e8-bb82-4115-8e77-278960bd50ab</RequestId>
  </ResponseMetadata>
</CreateStackResponse>
```

```console
2020-08-13T13:31:34-07:00 [ℹ]  deploying stack "eksctl-prototype-cluster"
2020-08-13T13:31:34-07:00 [▶]  start waiting for CloudFormation stack "eksctl-prototype-cluster"
2020-08-13T13:31:34-07:00 [▶]  waiting for CloudFormation stack "eksctl-prototype-cluster"
2020-08-13T13:31:34-07:00 [▶]  DEBUG: Request cloudformation/DescribeStacks Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64) Waiter
Content-Length: 176
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=8800e8ab86bb3410a1c7a46017580c65b79a456e275f90d039a80bacd7cb5509
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T203134Z
Accept-Encoding: gzip
-----------------------------------------------------
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Content-Length: 1959
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:31:34 GMT
X-Amzn-Requestid: bd6e5b80-38bd-4aa4-837b-6127f01546d7
-----------------------------------------------------
```

```xml
<DescribeStacksResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <DescribeStacksResult>
    <Stacks>
      <member>
        <Capabilities>
          <member>CAPABILITY_IAM</member>
        </Capabilities>
        <CreationTime>2020-08-13T20:31:34.071Z</CreationTime>
        <NotificationARNs/>
        <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</StackId>
        <StackName>eksctl-prototype-cluster</StackName>
        <Description>EKS cluster (dedicated VPC: true, dedicated IAM: true) [created and managed by eksctl]</Description>
        <StackStatus>CREATE_IN_PROGRESS</StackStatus>
        <DisableRollback>false</DisableRollback>
        <Tags>
          <member>
            <Value>prototype</Value>
            <Key>alpha.eksctl.io/cluster-name</Key>
          </member>
          <member>
            <Value>Infrastructure</Value>
            <Key>Owner</Key>
          </member>
          <member>
            <Value>prototype</Value>
            <Key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</Key>
          </member>
          <member>
            <Value>DevOps Team</Value>
            <Key>Team</Key>
          </member>
          <member>
            <Value>Eduardo Valdes</Value>
            <Key>Creator</Key>
          </member>
          <member>
            <Value>0.25.0</Value>
            <Key>alpha.eksctl.io/eksctl-version</Key>
          </member>
        </Tags>
        <RollbackConfiguration/>
        <DriftInformation>
          <StackDriftStatus>NOT_CHECKED</StackDriftStatus>
        </DriftInformation>
        <EnableTerminationProtection>false</EnableTerminationProtection>
        <StackStatusReason>User Initiated</StackStatusReason>
      </member>
    </Stacks>
  </DescribeStacksResult>
  <ResponseMetadata>
    <RequestId>bd6e5b80-38bd-4aa4-837b-6127f01546d7</RequestId>
  </ResponseMetadata>
</DescribeStacksResponse>
```

```console
2020-08-13T13:42:43-07:00 [▶]  waiting for CloudFormation stack "eksctl-prototype-cluster"
2020-08-13T13:42:43-07:00 [▶]  DEBUG: Request cloudformation/DescribeStacks Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64) Waiter
Content-Length: 176
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=741294ba85dfa3266c9e6efcbe7beddd5141b9e8df572c4d403c0ea11d607dea
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204243Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:42:42 GMT
Vary: accept-encoding
X-Amzn-Requestid: 13228961-25fb-413d-98c0-58115463b8d3
```

```xml
<DescribeStacksResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <DescribeStacksResult>
    <Stacks>
      <member>
        <Outputs>
          <member>
            <ExportName>eksctl-prototype-cluster::SubnetsPrivate</ExportName>
            <OutputKey>SubnetsPrivate</OutputKey>
            <OutputValue>subnet-0c8745dead9e6ad94,subnet-01f0c768fca0cdd73,subnet-043a3e50cf9e9da34</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::SubnetsPublic</ExportName>
            <OutputKey>SubnetsPublic</OutputKey>
            <OutputValue>subnet-07a588c63b48da4e1,subnet-03399f59f0f174044,subnet-0788533b3af3ff72c</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::ServiceRoleARN</ExportName>
            <OutputKey>ServiceRoleARN</OutputKey>
            <OutputValue>arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-11WWHVBHUS8SU</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::VPC</ExportName>
            <OutputKey>VPC</OutputKey>
            <OutputValue>vpc-0fbc47be0823afa5c</OutputValue>
          </member>
          <member>
            <OutputKey>ClusterStackName</OutputKey>
            <OutputValue>eksctl-prototype-cluster</OutputValue>
          </member>
          <member>
            <OutputKey>CertificateAuthorityData</OutputKey>
            <OutputValue>LS0tLS1CRU ... UtLS0tLQo=</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::SecurityGroup</ExportName>
            <OutputKey>SecurityGroup</OutputKey>
            <OutputValue>sg-03333ef6a52a9493b</OutputValue>
          </member>
          <member>
            <OutputKey>FeatureNATMode</OutputKey>
            <OutputValue>Single</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::Endpoint</ExportName>
            <OutputKey>Endpoint</OutputKey>
            <OutputValue>https://19099E1AA03B92443BA10641A6F620B7.gr7.us-west-2.eks.amazonaws.com</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::SharedNodeSecurityGroup</ExportName>
            <OutputKey>SharedNodeSecurityGroup</OutputKey>
            <OutputValue>sg-07f40333322755358</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::ClusterSecurityGroupId</ExportName>
            <OutputKey>ClusterSecurityGroupId</OutputKey>
            <OutputValue>sg-00491127f0c474582</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::ARN</ExportName>
            <OutputKey>ARN</OutputKey>
            <OutputValue>arn:aws:eks:us-west-2:738054984624:cluster/prototype</OutputValue>
          </member>
          <member>
            <ExportName>eksctl-prototype-cluster::FargatePodExecutionRoleARN</ExportName>
            <OutputKey>FargatePodExecutionRoleARN</OutputKey>
            <OutputValue>arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS</OutputValue>
          </member>
        </Outputs>
        <Capabilities>
          <member>CAPABILITY_IAM</member>
        </Capabilities>
        <CreationTime>2020-08-13T20:31:34.071Z</CreationTime>
        <NotificationARNs/>
        <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</StackId>
        <StackName>eksctl-prototype-cluster</StackName>
        <Description>EKS cluster (dedicated VPC: true, dedicated IAM: true) [created and managed by eksctl]</Description>
        <StackStatus>CREATE_COMPLETE</StackStatus>
        <DisableRollback>false</DisableRollback>
        <Tags>
          <member>
            <Value>prototype</Value>
            <Key>alpha.eksctl.io/cluster-name</Key>
          </member>
          <member>
            <Value>Infrastructure</Value>
            <Key>Owner</Key>
          </member>
          <member>
            <Value>prototype</Value>
            <Key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</Key>
          </member>
          <member>
            <Value>DevOps Team</Value>
            <Key>Team</Key>
          </member>
          <member>
            <Value>Eduardo Valdes</Value>
            <Key>Creator</Key>
          </member>
          <member>
            <Value>0.25.0</Value>
            <Key>alpha.eksctl.io/eksctl-version</Key>
          </member>
        </Tags>
        <RollbackConfiguration/>
        <DriftInformation>
          <StackDriftStatus>NOT_CHECKED</StackDriftStatus>
        </DriftInformation>
        <EnableTerminationProtection>false</EnableTerminationProtection>
      </member>
    </Stacks>
  </DescribeStacksResult>
  <ResponseMetadata>
    <RequestId>13228961-25fb-413d-98c0-58115463b8d3</RequestId>
  </ResponseMetadata>
</DescribeStacksResponse>
```

```console
2020-08-13T13:42:43-07:00 [▶]  processing stack outputs
2020-08-13T13:42:43-07:00 [▶]  DEBUG: Request ec2/DescribeSubnets Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 149
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=274fd71913718209cb3f2ce4cd7c1050e5e2058b53ea0770d16cae06970b6e22
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204243Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml;charset=UTF-8
Date: Thu, 13 Aug 2020 20:42:43 GMT
Server: AmazonEC2
Vary: accept-encoding
X-Amzn-Requestid: 5e9d9541-db70-4ae0-b0c2-b71b7a7b6f1c
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DescribeSubnetsResponse xmlns="http://ec2.amazonaws.com/doc/2016-11-15/">
    <requestId>5e9d9541-db70-4ae0-b0c2-b71b7a7b6f1c</requestId>
    <subnetSet>
        <item>
            <subnetId>subnet-01f0c768fca0cdd73</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-01f0c768fca0cdd73</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.128.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8187</availableIpAddressCount>
            <availabilityZone>us-west-2b</availabilityZone>
            <availabilityZoneId>usw2-az1</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>false</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPrivateUSWEST2B</value>
                </item>
                <item>
                    <key>kubernetes.io/role/internal-elb</key>
                    <value>1</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPrivateUSWEST2B</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
        <item>
            <subnetId>subnet-043a3e50cf9e9da34</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-043a3e50cf9e9da34</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.160.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8186</availableIpAddressCount>
            <availabilityZone>us-west-2c</availabilityZone>
            <availabilityZoneId>usw2-az3</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>false</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPrivateUSWEST2C</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>kubernetes.io/role/internal-elb</key>
                    <value>1</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPrivateUSWEST2C</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
        <item>
            <subnetId>subnet-0c8745dead9e6ad94</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-0c8745dead9e6ad94</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.96.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8187</availableIpAddressCount>
            <availabilityZone>us-west-2a</availabilityZone>
            <availabilityZoneId>usw2-az2</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>false</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPrivateUSWEST2A</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPrivateUSWEST2A</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>kubernetes.io/role/internal-elb</key>
                    <value>1</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
    </subnetSet>
</DescribeSubnetsResponse>
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 68
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=db75b29f88d81e0f45d31374d447806434a5ee6897390753d198f9cd11ab85e8
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204243Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml;charset=UTF-8
Date: Thu, 13 Aug 2020 20:42:43 GMT
Server: AmazonEC2
Vary: accept-encoding
X-Amzn-Requestid: 284aec05-1871-48ea-9799-2483781c836f
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DescribeVpcsResponse xmlns="http://ec2.amazonaws.com/doc/2016-11-15/">
    <requestId>284aec05-1871-48ea-9799-2483781c836f</requestId>
    <vpcSet>
        <item>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <ownerId>738054984624</ownerId>
            <state>available</state>
            <cidrBlock>192.168.0.0/16</cidrBlock>
            <cidrBlockAssociationSet>
                <item>
                    <cidrBlock>192.168.0.0/16</cidrBlock>
                    <associationId>vpc-cidr-assoc-093af107d3196f828</associationId>
                    <cidrBlockState>
                        <state>associated</state>
                    </cidrBlockState>
                </item>
            </cidrBlockAssociationSet>
            <dhcpOptionsId>dopt-df908bbd</dhcpOptionsId>
            <tagSet>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>VPC</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/VPC</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
            </tagSet>
            <instanceTenancy>default</instanceTenancy>
            <isDefault>false</isDefault>
        </item>
    </vpcSet>
</DescribeVpcsResponse>
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 149
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=b542cfe3388f14736286c38707617078f52fc3a5bf3eeb1d181d5c8031ce9fe5
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204244Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml;charset=UTF-8
Date: Thu, 13 Aug 2020 20:42:43 GMT
Server: AmazonEC2
Vary: accept-encoding
X-Amzn-Requestid: 030c5845-ebf8-48da-b996-f890f011755c
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DescribeSubnetsResponse xmlns="http://ec2.amazonaws.com/doc/2016-11-15/">
    <requestId>030c5845-ebf8-48da-b996-f890f011755c</requestId>
    <subnetSet>
        <item>
            <subnetId>subnet-07a588c63b48da4e1</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-07a588c63b48da4e1</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.32.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8187</availableIpAddressCount>
            <availabilityZone>us-west-2b</availabilityZone>
            <availabilityZoneId>usw2-az1</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>true</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPublicUSWEST2B</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPublicUSWEST2B</value>
                </item>
                <item>
                    <key>kubernetes.io/role/elb</key>
                    <value>1</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
        <item>
            <subnetId>subnet-0788533b3af3ff72c</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-0788533b3af3ff72c</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.0.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8186</availableIpAddressCount>
            <availabilityZone>us-west-2a</availabilityZone>
            <availabilityZoneId>usw2-az2</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>true</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
                <item>
                    <key>kubernetes.io/role/elb</key>
                    <value>1</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPublicUSWEST2A</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPublicUSWEST2A</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
        <item>
            <subnetId>subnet-03399f59f0f174044</subnetId>
            <subnetArn>arn:aws:ec2:us-west-2:738054984624:subnet/subnet-03399f59f0f174044</subnetArn>
            <state>available</state>
            <ownerId>738054984624</ownerId>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <cidrBlock>192.168.64.0/19</cidrBlock>
            <ipv6CidrBlockAssociationSet/>
            <availableIpAddressCount>8187</availableIpAddressCount>
            <availabilityZone>us-west-2c</availabilityZone>
            <availabilityZoneId>usw2-az3</availabilityZoneId>
            <defaultForAz>false</defaultForAz>
            <mapPublicIpOnLaunch>true</mapPublicIpOnLaunch>
            <tagSet>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/SubnetPublicUSWEST2C</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>SubnetPublicUSWEST2C</value>
                </item>
                <item>
                    <key>kubernetes.io/cluster/prototype</key>
                    <value>shared</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>kubernetes.io/role/elb</key>
                    <value>1</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
            </tagSet>
            <assignIpv6AddressOnCreation>false</assignIpv6AddressOnCreation>
            <mapCustomerOwnedIpOnLaunch>false</mapCustomerOwnedIpOnLaunch>
        </item>
    </subnetSet>
</DescribeSubnetsResponse>
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: ec2.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 68
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/ec2/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=dd4ad827d493716531c9e43bc71bd86611189d0527584597db25907339e1a8c4
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204244Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml;charset=UTF-8
Date: Thu, 13 Aug 2020 20:42:43 GMT
Server: AmazonEC2
Vary: accept-encoding
X-Amzn-Requestid: 3acb65a5-fdad-4b49-8b4f-bd25dfc9b341
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<DescribeVpcsResponse xmlns="http://ec2.amazonaws.com/doc/2016-11-15/">
    <requestId>3acb65a5-fdad-4b49-8b4f-bd25dfc9b341</requestId>
    <vpcSet>
        <item>
            <vpcId>vpc-0fbc47be0823afa5c</vpcId>
            <ownerId>738054984624</ownerId>
            <state>available</state>
            <cidrBlock>192.168.0.0/16</cidrBlock>
            <cidrBlockAssociationSet>
                <item>
                    <cidrBlock>192.168.0.0/16</cidrBlock>
                    <associationId>vpc-cidr-assoc-093af107d3196f828</associationId>
                    <cidrBlockState>
                        <state>associated</state>
                    </cidrBlockState>
                </item>
            </cidrBlockAssociationSet>
            <dhcpOptionsId>dopt-df908bbd</dhcpOptionsId>
            <tagSet>
                <item>
                    <key>aws:cloudformation:stack-id</key>
                    <value>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-cluster/fa6481c0-dda3-11ea-8941-0613825de49c</value>
                </item>
                <item>
                    <key>aws:cloudformation:logical-id</key>
                    <value>VPC</value>
                </item>
                <item>
                    <key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Name</key>
                    <value>eksctl-prototype-cluster/VPC</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/cluster-name</key>
                    <value>prototype</value>
                </item>
                <item>
                    <key>Owner</key>
                    <value>Infrastructure</value>
                </item>
                <item>
                    <key>Creator</key>
                    <value>Eduardo Valdes</value>
                </item>
                <item>
                    <key>alpha.eksctl.io/eksctl-version</key>
                    <value>0.25.0</value>
                </item>
                <item>
                    <key>aws:cloudformation:stack-name</key>
                    <value>eksctl-prototype-cluster</value>
                </item>
                <item>
                    <key>Team</key>
                    <value>DevOps Team</value>
                </item>
            </tagSet>
            <instanceTenancy>default</instanceTenancy>
            <isDefault>false</isDefault>
        </item>
    </vpcSet>
</DescribeVpcsResponse>
```

```console
2020-08-13T13:42:44-07:00 [▶]  completed task: create cluster control plane "prototype"
2020-08-13T13:42:44-07:00 [▶]  started task: 2 sequential sub-tasks: { 2 sequential sub-tasks: { tag cluster, create fargate profiles }, create managed nodegroup "devops" }
2020-08-13T13:42:44-07:00 [▶]  started task: 2 sequential sub-tasks: { tag cluster, create fargate profiles }
2020-08-13T13:42:44-07:00 [▶]  started task: tag cluster
2020-08-13T13:42:44-07:00 [▶]  DEBUG: Request eks/DescribeCluster Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
GET /clusters/prototype HTTP/1.1
Host: eks.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/eks/aws4_request, SignedHeaders=content-type;host;x-amz-date, Signature=d66fa08642c73ae50147616f26d55af0770efb46ed8d3f68a5e8cb2fd986889c
Content-Type: application/json
X-Amz-Date: 20200813T204244Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/2.0 200 OK
Content-Length: 2795
Content-Type: application/json
Date: Thu, 13 Aug 2020 20:42:44 GMT
X-Amz-Apigw-Id: RObWtEDQPHcF5Og=
X-Amzn-Requestid: 8d96ce8f-f1da-4359-802e-7a7d2d151258
X-Amzn-Trace-Id: Root=1-5f35a5c4-2fc2dbb5d8f2beea000b4eee
```

```json
{
  "cluster" : {
    "name" : "prototype",
    "arn" : "arn:aws:eks:us-west-2:738054984624:cluster/prototype",
    "createdAt" : 1.597350762619E9,
    "version" : "1.15",
    "endpoint" : "https://19099E1AA03B92443BA10641A6F620B7.gr7.us-west-2.eks.amazonaws.com",
    "roleArn" : "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-11WWHVBHUS8SU",
    "resourcesVpcConfig" : {
      "subnetIds" : [ "subnet-07a588c63b48da4e1", "subnet-03399f59f0f174044", "subnet-0788533b3af3ff72c", "subnet-0c8745dead9e6ad94", "subnet-01f0c768fca0cdd73", "subnet-043a3e50cf9e9da34" ],
      "securityGroupIds" : [ "sg-03333ef6a52a9493b" ],
      "clusterSecurityGroupId" : "sg-00491127f0c474582",
      "vpcId" : "vpc-0fbc47be0823afa5c",
      "endpointPublicAccess" : true,
      "endpointPrivateAccess" : false,
      "publicAccessCidrs" : [ "0.0.0.0/0" ]
    },
    "kubernetesNetworkConfig" : null,
    "logging" : {
      "clusterLogging" : [ {
        "types" : [ "api", "audit", "authenticator", "controllerManager", "scheduler" ],
        "enabled" : false
      } ]
    },
    "identity" : {
      "oidc" : {
        "issuer" : "https://oidc.eks.us-west-2.amazonaws.com/id/19099E1AA03B92443BA10641A6F620B7"
      }
    },
    "status" : "ACTIVE",
    "certificateAuthority" : {
      "data" : "LS0tLS1CRU ... UtLS0tLQo="
    },
    "clientRequestToken" : null,
    "platformVersion" : "eks.4",
    "tags" : { },
    "encryptionConfig" : null
  }
}
```

```json
{
  "Arn": "arn:aws:eks:us-west-2:738054984624:cluster/prototype",
  "CertificateAuthority": {
    "Data": "LS0tLS1CRU ... UtLS0tLQo="
  },
  "CreatedAt": 2020-08-13 20:32:42 +0000 UTC,
  "Endpoint": "https://19099E1AA03B92443BA10641A6F620B7.gr7.us-west-2.eks.amazonaws.com",
  "Identity": {
    "Oidc": {
      "Issuer": "https://oidc.eks.us-west-2.amazonaws.com/id/19099E1AA03B92443BA10641A6F620B7"
    }
  },
  "Logging": {
    "ClusterLogging": [{
        "Enabled": false,
        "Types": [
          "api",
          "audit",
          "authenticator",
          "controllerManager",
          "scheduler"
        ]
      }]
  },
  "Name": "prototype",
  "PlatformVersion": "eks.4",
  "ResourcesVpcConfig": {
    "ClusterSecurityGroupId": "sg-00491127f0c474582",
    "EndpointPrivateAccess": false,
    "EndpointPublicAccess": true,
    "PublicAccessCidrs": ["0.0.0.0/0"],
    "SecurityGroupIds": ["sg-03333ef6a52a9493b"],
    "SubnetIds": [
      "subnet-07a588c63b48da4e1",
      "subnet-03399f59f0f174044",
      "subnet-0788533b3af3ff72c",
      "subnet-0c8745dead9e6ad94",
      "subnet-01f0c768fca0cdd73",
      "subnet-043a3e50cf9e9da34"
    ],
    "VpcId": "vpc-0fbc47be0823afa5c"
  },
  "RoleArn": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-11WWHVBHUS8SU",
  "Status": "ACTIVE",
  "Tags": {

  },
  "Version": "1.15"
}
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST /tags/arn%!!Aaws%!!Aeks%!!Aus-west-2%!!A738054984624%!!Acluster%!!Fprototype HTTP/1.1
Host: eks.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 83
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/eks/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=d69c1700d3c8fa8365f4adc4d098b3b3941aa9678747ab6a35ea405e1a7f4e66
Content-Type: application/json
X-Amz-Date: 20200813T204244Z
Accept-Encoding: gzip

{"tags":{"Creator":"Eduardo Valdes","Owner":"Infrastructure","Team":"DevOps Team"}}
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/2.0 204 No Content
Content-Length: 0
Access-Control-Allow-Origin: *
Date: Thu, 13 Aug 2020 20:42:44 GMT
X-Amz-Apigw-Id: RObWuGVxvHcF-JA=
X-Amzn-Requestid: fc5ec207-5b6c-4130-9a71-c61bbf104b25
X-Amzn-Trace-Id: Root=1-5f35a5c4-7df5ced2e2b8b58d7ef00503
```

```console
2020-08-13T13:42:44-07:00 [✔]  tagged EKS cluster (Owner=Infrastructure, Team=DevOps Team, Creator=Eduardo Valdes)
2020-08-13T13:42:44-07:00 [▶]  completed task: tag cluster
2020-08-13T13:42:44-07:00 [▶]  started task: create fargate profiles
2020-08-13T13:42:44-07:00 [ℹ]  creating Fargate profile "fp-default" on EKS cluster "prototype"
2020-08-13T13:42:44-07:00 [▶]  Fargate profile: create request input: &v1alpha5.FargateProfile{Name:"fp-default", PodExecutionRoleARN:"arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS", Selectors:[]v1alpha5.FargateProfileSelector{v1alpha5.FargateProfileSelector{Namespace:"default", Labels:map[string]string(nil)}, v1alpha5.FargateProfileSelector{Namespace:"kube-system", Labels:map[string]string(nil)}}, Subnets:[]string(nil), Tags:map[string]string(nil)}
2020-08-13T13:42:44-07:00 [▶]  Fargate profile: create request: sending:
```

```json
{
  "ClusterName": "prototype",
  "FargateProfileName": "fp-default",
  "PodExecutionRoleArn": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
  "Selectors": [{
      "Namespace": "default"
    },{
      "Namespace": "kube-system"
    }]
}
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST /clusters/prototype/fargate-profiles HTTP/1.1
Host: eks.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 276
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/eks/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=c186fcd3c70ab46e42a73c53795998c3beec47cd28a08048274f8907b683cff0
Content-Type: application/json
X-Amz-Date: 20200813T204244Z
Accept-Encoding: gzip

{"clientRequestToken":"17513D81-21F5-4535-A157-6CF74C126649","fargateProfileName":"fp-default","podExecutionRoleArn":"arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS","selectors":[{"namespace":"default"},{"namespace":"kube-system"}]}
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/2.0 200 OK
Content-Length: 693
Content-Type: application/json
Date: Thu, 13 Aug 2020 20:42:46 GMT
X-Amz-Apigw-Id: RObWwEnpPHcF7GA=
X-Amzn-Requestid: c64b19f0-425d-4806-bd6e-7c2f0a1c6504
X-Amzn-Trace-Id: Root=1-5f35a5c4-852f06e661e4a13764d7fa7d
```

```json
{
  "fargateProfile" : {
    "fargateProfileName" : "fp-default",
    "fargateProfileArn" : "arn:aws:eks:us-west-2:738054984624:fargateprofile/prototype/fp-default/16b9f4c7-c44e-2440-94ed-997977a9fb9e",
    "clusterName" : "prototype",
    "createdAt" : 1.597351366588E9,
    "podExecutionRoleArn" : "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
    "subnets" : [ "subnet-01f0c768fca0cdd73", "subnet-043a3e50cf9e9da34", "subnet-0c8745dead9e6ad94" ],
    "selectors" : [ {
      "namespace" : "default",
      "labels" : null
    }, {
      "namespace" : "kube-system",
      "labels" : null
    } ],
    "status" : "CREATING",
    "tags" : { }
  }
}
```

```json
{
  "FargateProfile": {
    "ClusterName": "prototype",
    "CreatedAt": "2020-08-13 20:42:46 +0000 UTC",
    "FargateProfileArn": "arn:aws:eks:us-west-2:738054984624:fargateprofile/prototype/fp-default/16b9f4c7-c44e-2440-94ed-997977a9fb9e",
    "FargateProfileName": "fp-default",
    "PodExecutionRoleArn": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
    "Selectors": [{
        "Namespace": "default"
      },{
        "Namespace": "kube-system"
      }],
    "Status": "CREATING",
    "Subnets": ["subnet-01f0c768fca0cdd73","subnet-043a3e50cf9e9da34","subnet-0c8745dead9e6ad94"],
    "Tags": {

    }
  }
}
```

```json
{
  "ClusterName": "prototype",
  "FargateProfileName": "fp-default"
}
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
GET /clusters/prototype/fargate-profiles/fp-default HTTP/1.1
Host: eks.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/eks/aws4_request, SignedHeaders=content-type;host;x-amz-date, Signature=f23eb421d5b4229173520dde975fc90d3578991f94c11666433e61abd4cfdfe4
Content-Type: application/json
X-Amz-Date: 20200813T204454Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/2.0 200 OK
Content-Length: 691
Content-Type: application/json
Date: Thu, 13 Aug 2020 20:44:54 GMT
X-Amz-Apigw-Id: RObrDFmJPHcFa5w=
X-Amzn-Requestid: bcf0c4ed-5628-49fd-a5da-8b0e12e16288
X-Amzn-Trace-Id: Root=1-5f35a646-13f84bc90fb0225c865f466e
```

```json
{
  "fargateProfile" : {
    "fargateProfileName" : "fp-default",
    "fargateProfileArn" : "arn:aws:eks:us-west-2:738054984624:fargateprofile/prototype/fp-default/16b9f4c7-c44e-2440-94ed-997977a9fb9e",
    "clusterName" : "prototype",
    "createdAt" : 1.597351366588E9,
    "podExecutionRoleArn" : "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
    "subnets" : [ "subnet-01f0c768fca0cdd73", "subnet-043a3e50cf9e9da34", "subnet-0c8745dead9e6ad94" ],
    "selectors" : [ {
      "namespace" : "default",
      "labels" : null
    }, {
      "namespace" : "kube-system",
      "labels" : null
    } ],
    "status" : "ACTIVE",
    "tags" : { }
  }
}
```

```json
{
  "FargateProfile": {
    "ClusterName": "prototype",
    "CreatedAt": "2020-08-13 20:42:46 +0000 UTC",
    "FargateProfileArn": "arn:aws:eks:us-west-2:738054984624:fargateprofile/prototype/fp-default/16b9f4c7-c44e-2440-94ed-997977a9fb9e",
    "FargateProfileName": "fp-default",
    "PodExecutionRoleArn": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
    "Selectors": [{
        "Namespace": "default"
      },{
        "Namespace": "kube-system"
      }],
    "Status": "ACTIVE",
    "Subnets": ["subnet-01f0c768fca0cdd73","subnet-043a3e50cf9e9da34","subnet-0c8745dead9e6ad94"],
    "Tags": {

    }
  }
}
```

```console
2020-08-13T13:44:54-07:00 [ℹ]  created Fargate profile "fp-default" on EKS cluster "prototype"
2020-08-13T13:44:55-07:00 [▶]  deployment "coredns" with compute type "ec2" currently has 0/2 replicas running
2020-08-13T13:44:55-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:44:55-07:00 [ℹ]  "coredns" is now schedulable onto Fargate
2020-08-13T13:44:55-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:44:55-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:44:56-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:44:56-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:44:58-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:44:58-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:45:02-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:45:02-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:45:10-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:45:10-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:45:26-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 0/2 replicas running
2020-08-13T13:45:26-07:00 [▶]  pod "coredns-5f897d799c-2fp98" with compute type "ec2" and status "Pending" is scheduled on ""
2020-08-13T13:45:58-07:00 [▶]  deployment "coredns" with compute type "fargate" currently has 2/2 replicas running
2020-08-13T13:45:58-07:00 [ℹ]  "coredns" is now scheduled onto Fargate
2020-08-13T13:45:58-07:00 [▶]  pod "coredns-8696bc9677-nrltl" with compute type "fargate" and status "Running" is scheduled on "fargate-ip-192-168-152-198.us-west-2.compute.internal"
2020-08-13T13:45:58-07:00 [▶]  pod "coredns-8696bc9677-smlsc" with compute type "fargate" and status "Running" is scheduled on "fargate-ip-192-168-111-249.us-west-2.compute.internal"
2020-08-13T13:45:58-07:00 [ℹ]  "coredns" pods are now scheduled onto Fargate
2020-08-13T13:45:58-07:00 [▶]  completed task: create fargate profiles
2020-08-13T13:45:58-07:00 [▶]  completed task: 2 sequential sub-tasks: { tag cluster, create fargate profiles }
2020-08-13T13:45:58-07:00 [▶]  started task: create managed nodegroup "devops"
2020-08-13T13:45:58-07:00 [▶]  waiting for 1 parallel tasks to complete
2020-08-13T13:45:58-07:00 [▶]  started task: create managed nodegroup "devops"
2020-08-13T13:45:58-07:00 [ℹ]  building managed nodegroup stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:45:58-07:00 [▶]  CreateStackInput =
```

```json
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "EKS Managed Nodes (SSH access: true) [created by eksctl]",
  "Mappings": {
    "ServicePrincipalPartitionMap": {
      "aws": {
        "EC2": "ec2.amazonaws.com",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      },
      "aws-cn": {
        "EC2": "ec2.amazonaws.com.cn",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      },
      "aws-us-gov": {
        "EC2": "ec2.amazonaws.com",
        "EKS": "eks.amazonaws.com",
        "EKSFargatePods": "eks-fargate-pods.amazonaws.com"
      }
    }
  },
  "Resources": {
    "ManagedNodeGroup": {
      "Type": "AWS::EKS::Nodegroup",
      "Properties": {
        "AmiType": "AL2_x86_64",
        "ClusterName": "prototype",
        "DiskSize": 80,
        "InstanceTypes": [
          "m5.large"
        ],
        "Labels": {
          "alpha.eksctl.io/cluster-name": "prototype",
          "alpha.eksctl.io/nodegroup-name": "devops"
        },
        "NodeRole": {
          "Fn::GetAtt": [
            "NodeInstanceRole",
            "Arn"
          ]
        },
        "NodegroupName": "devops",
        "RemoteAccess": {
          "Ec2SshKey": "eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0"
        },
        "ScalingConfig": {
          "DesiredSize": 2,
          "MaxSize": 3,
          "MinSize": 2
        },
        "Subnets": {
          "Fn::Split": [
            ",",
            {
              "Fn::ImportValue": "eksctl-prototype-cluster::SubnetsPublic"
            }
          ]
        },
        "Tags": {
          "alpha.eksctl.io/nodegroup-name": "devops",
          "alpha.eksctl.io/nodegroup-type": "managed"
        }
      }
    },
    "NodeInstanceRole": {
      "Type": "AWS::IAM::Role",
      "Properties": {
        "AssumeRolePolicyDocument": {
          "Statement": [
            {
              "Action": [
                "sts:AssumeRole"
              ],
              "Effect": "Allow",
              "Principal": {
                "Service": [
                  {
                    "Fn::FindInMap": [
                      "ServicePrincipalPartitionMap",
                      {
                        "Ref": "AWS::Partition"
                      },
                      "EC2"
                    ]
                  }
                ]
              }
            }
          ],
          "Version": "2012-10-17"
        },
        "ManagedPolicyArns": [
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEC2ContainerRegistryPowerUser"
          },
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEC2ContainerRegistryReadOnly"
          },
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEKSWorkerNodePolicy"
          },
          {
            "Fn::Sub": "arn:${AWS::Partition}:iam::aws:policy/AmazonEKS_CNI_Policy"
          }
        ],
        "Path": "/",
        "Tags": [
          {
            "Key": "Name",
            "Value": {
              "Fn::Sub": "${AWS::StackName}/NodeInstanceRole"
            }
          }
        ]
      }
    },
    "PolicyALBIngress": {
      "Type": "AWS::IAM::Policy",
      "Properties": {
        "PolicyDocument": {
          "Statement": [
            {
              "Action": [
                "acm:DescribeCertificate",
                "acm:ListCertificates",
                "acm:GetCertificate",
                "ec2:AuthorizeSecurityGroupIngress",
                "ec2:CreateSecurityGroup",
                "ec2:CreateTags",
                "ec2:DeleteTags",
                "ec2:DeleteSecurityGroup",
                "ec2:DescribeAccountAttributes",
                "ec2:DescribeAddresses",
                "ec2:DescribeInstances",
                "ec2:DescribeInstanceStatus",
                "ec2:DescribeInternetGateways",
                "ec2:DescribeNetworkInterfaces",
                "ec2:DescribeSecurityGroups",
                "ec2:DescribeSubnets",
                "ec2:DescribeTags",
                "ec2:DescribeVpcs",
                "ec2:ModifyInstanceAttribute",
                "ec2:ModifyNetworkInterfaceAttribute",
                "ec2:RevokeSecurityGroupIngress",
                "elasticloadbalancing:AddListenerCertificates",
                "elasticloadbalancing:AddTags",
                "elasticloadbalancing:CreateListener",
                "elasticloadbalancing:CreateLoadBalancer",
                "elasticloadbalancing:CreateRule",
                "elasticloadbalancing:CreateTargetGroup",
                "elasticloadbalancing:DeleteListener",
                "elasticloadbalancing:DeleteLoadBalancer",
                "elasticloadbalancing:DeleteRule",
                "elasticloadbalancing:DeleteTargetGroup",
                "elasticloadbalancing:DeregisterTargets",
                "elasticloadbalancing:DescribeListenerCertificates",
                "elasticloadbalancing:DescribeListeners",
                "elasticloadbalancing:DescribeLoadBalancers",
                "elasticloadbalancing:DescribeLoadBalancerAttributes",
                "elasticloadbalancing:DescribeRules",
                "elasticloadbalancing:DescribeSSLPolicies",
                "elasticloadbalancing:DescribeTags",
                "elasticloadbalancing:DescribeTargetGroups",
                "elasticloadbalancing:DescribeTargetGroupAttributes",
                "elasticloadbalancing:DescribeTargetHealth",
                "elasticloadbalancing:ModifyListener",
                "elasticloadbalancing:ModifyLoadBalancerAttributes",
                "elasticloadbalancing:ModifyRule",
                "elasticloadbalancing:ModifyTargetGroup",
                "elasticloadbalancing:ModifyTargetGroupAttributes",
                "elasticloadbalancing:RegisterTargets",
                "elasticloadbalancing:RemoveListenerCertificates",
                "elasticloadbalancing:RemoveTags",
                "elasticloadbalancing:SetIpAddressType",
                "elasticloadbalancing:SetSecurityGroups",
                "elasticloadbalancing:SetSubnets",
                "elasticloadbalancing:SetWebACL",
                "iam:CreateServiceLinkedRole",
                "iam:GetServerCertificate",
                "iam:ListServerCertificates",
                "waf-regional:GetWebACLForResource",
                "waf-regional:GetWebACL",
                "waf-regional:AssociateWebACL",
                "waf-regional:DisassociateWebACL",
                "tag:GetResources",
                "tag:TagResources",
                "waf:GetWebACL",
                "wafv2:GetWebACL",
                "wafv2:GetWebACLForResource",
                "wafv2:AssociateWebACL",
                "wafv2:DisassociateWebACL",
                "shield:DescribeProtection",
                "shield:GetSubscriptionState",
                "shield:DeleteProtection",
                "shield:CreateProtection",
                "shield:DescribeSubscription",
                "shield:ListProtections"
              ],
              "Effect": "Allow",
              "Resource": "*"
            }
          ],
          "Version": "2012-10-17"
        },
        "PolicyName": {
          "Fn::Sub": "${AWS::StackName}-PolicyALBIngress"
        },
        "Roles": [
          {
            "Ref": "NodeInstanceRole"
          }
        ]
      }
    },
    "PolicyAppMesh": {
      "Type": "AWS::IAM::Policy",
      "Properties": {
        "PolicyDocument": {
          "Statement": [
            {
              "Action": [
                "servicediscovery:CreateService",
                "servicediscovery:DeleteService",
                "servicediscovery:GetService",
                "servicediscovery:GetInstance",
                "servicediscovery:RegisterInstance",
                "servicediscovery:DeregisterInstance",
                "servicediscovery:ListInstances",
                "servicediscovery:ListNamespaces",
                "servicediscovery:ListServices",
                "servicediscovery:GetInstancesHealthStatus",
                "servicediscovery:UpdateInstanceCustomHealthStatus",
                "servicediscovery:GetOperation",
                "route53:GetHealthCheck",
                "route53:CreateHealthCheck",
                "route53:UpdateHealthCheck",
                "route53:ChangeResourceRecordSets",
                "route53:DeleteHealthCheck",
                "appmesh:*"
              ],
              "Effect": "Allow",
              "Resource": "*"
            }
          ],
          "Version": "2012-10-17"
        },
        "PolicyName": {
          "Fn::Sub": "${AWS::StackName}-PolicyAppMesh"
        },
        "Roles": [
          {
            "Ref": "NodeInstanceRole"
          }
        ]
      }
    },
    "PolicyAutoScaling": {
      "Type": "AWS::IAM::Policy",
      "Properties": {
        "PolicyDocument": {
          "Statement": [
            {
              "Action": [
                "autoscaling:DescribeAutoScalingGroups",
                "autoscaling:DescribeAutoScalingInstances",
                "autoscaling:DescribeLaunchConfigurations",
                "autoscaling:DescribeTags",
                "autoscaling:SetDesiredCapacity",
                "autoscaling:TerminateInstanceInAutoScalingGroup",
                "ec2:DescribeLaunchTemplateVersions"
              ],
              "Effect": "Allow",
              "Resource": "*"
            }
          ],
          "Version": "2012-10-17"
        },
        "PolicyName": {
          "Fn::Sub": "${AWS::StackName}-PolicyAutoScaling"
        },
        "Roles": [
          {
            "Ref": "NodeInstanceRole"
          }
        ]
      }
    }
  }
}
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 13396
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=7b72cd1110550706566ae81591092014d6177c2c4a7b598575ec95bd559a416e
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204558Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Content-Length: 401
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:46:04 GMT
X-Amzn-Requestid: 384f7dbb-4517-42a3-94e9-007ff4b5851d
```

```xml
<CreateStackResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <CreateStackResult>
    <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-nodegroup-devops/0153cc00-dda6-11ea-b1af-066ac882f2e8</StackId>
  </CreateStackResult>
  <ResponseMetadata>
    <RequestId>384f7dbb-4517-42a3-94e9-007ff4b5851d</RequestId>
  </ResponseMetadata>
</CreateStackResponse>
```

```console
2020-08-13T13:46:04-07:00 [ℹ]  deploying stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:46:04-07:00 [▶]  start waiting for CloudFormation stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:46:04-07:00 [▶]  waiting for CloudFormation stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:46:04-07:00 [▶]  DEBUG: Request cloudformation/DescribeStacks Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64) Waiter
Content-Length: 185
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=a90ff9c125388b094ad8b356805ca69b117f49e0e412223a08c5e84bec6bd25e
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204604Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:46:04 GMT
Vary: accept-encoding
X-Amzn-Requestid: c7330819-a2cb-4d56-8aab-c11dab5273bc
```

```xml
<DescribeStacksResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <DescribeStacksResult>
    <Stacks>
      <member>
        <Capabilities>
          <member>CAPABILITY_IAM</member>
        </Capabilities>
        <CreationTime>2020-08-13T20:46:04.543Z</CreationTime>
        <NotificationARNs/>
        <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-nodegroup-devops/0153cc00-dda6-11ea-b1af-066ac882f2e8</StackId>
        <StackName>eksctl-prototype-nodegroup-devops</StackName>
        <Description>EKS Managed Nodes (SSH access: true) [created by eksctl]</Description>
        <StackStatus>CREATE_IN_PROGRESS</StackStatus>
        <DisableRollback>false</DisableRollback>
        <Tags>
          <member>
            <Value>prototype</Value>
            <Key>alpha.eksctl.io/cluster-name</Key>
          </member>
          <member>
            <Value>Infrastructure</Value>
            <Key>Owner</Key>
          </member>
          <member>
            <Value>devops</Value>
            <Key>alpha.eksctl.io/nodegroup-name</Key>
          </member>
          <member>
            <Value>prototype</Value>
            <Key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</Key>
          </member>
          <member>
            <Value>DevOps Team</Value>
            <Key>Team</Key>
          </member>
          <member>
            <Value>managed</Value>
            <Key>alpha.eksctl.io/nodegroup-type</Key>
          </member>
          <member>
            <Value>Eduardo Valdes</Value>
            <Key>Creator</Key>
          </member>
          <member>
            <Value>0.25.0</Value>
            <Key>alpha.eksctl.io/eksctl-version</Key>
          </member>
        </Tags>
        <RollbackConfiguration/>
        <DriftInformation>
          <StackDriftStatus>NOT_CHECKED</StackDriftStatus>
        </DriftInformation>
        <EnableTerminationProtection>false</EnableTerminationProtection>
        <StackStatusReason>User Initiated</StackStatusReason>
      </member>
    </Stacks>
  </DescribeStacksResult>
  <ResponseMetadata>
    <RequestId>c7330819-a2cb-4d56-8aab-c11dab5273bc</RequestId>
  </ResponseMetadata>
</DescribeStacksResponse>
```

```console
2020-08-13T13:46:21-07:00 [▶]  waiting for CloudFormation stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:46:21-07:00 [▶]  DEBUG: Request cloudformation/DescribeStacks Details:
```

```console
2020-08-13T13:49:19-07:00 [▶]  done after 3m14.746903307s of waiting for CloudFormation stack "eksctl-prototype-nodegroup-devops"
2020-08-13T13:49:19-07:00 [▶]  DEBUG: Request cloudformation/DescribeStacks Details:
```

```console
---[ REQUEST POST-SIGN ]-----------------------------
POST / HTTP/1.1
Host: cloudformation.us-west-2.amazonaws.com
User-Agent: eksctl/{"Version":"0.25.0","PreReleaseID":"","Metadata":{"BuildDate":"2020-07-31T18:43:21Z","GitCommit":"673de795"},"EKSServerSupportedVersions":["1.14","1.15","1.16","1.17"]} aws-sdk-go/1.30.11 (go1.14.2; darwin; amd64)
Content-Length: 185
Authorization: AWS4-HMAC-SHA256 Credential=********************/20200813/us-west-2/cloudformation/aws4_request, SignedHeaders=content-length;content-type;host;x-amz-date, Signature=3866b0ce2f644688f4bcb0782a7a19a0333305510b128a5cf76c5ae5c6072a95
Content-Type: application/x-www-form-urlencoded; charset=utf-8
X-Amz-Date: 20200813T204919Z
Accept-Encoding: gzip
```

```console
---[ RESPONSE ]--------------------------------------
HTTP/1.1 200 OK
Transfer-Encoding: chunked
Content-Type: text/xml
Date: Thu, 13 Aug 2020 20:49:18 GMT
Vary: accept-encoding
X-Amzn-Requestid: e1f4c8e6-d7d1-472e-8c4c-f7092cc456e0
```

```xml
<DescribeStacksResponse xmlns="http://cloudformation.amazonaws.com/doc/2010-05-15/">
  <DescribeStacksResult>
    <Stacks>
      <member>
        <Capabilities>
          <member>CAPABILITY_IAM</member>
        </Capabilities>
        <CreationTime>2020-08-13T20:46:04.543Z</CreationTime>
        <NotificationARNs/>
        <StackId>arn:aws:cloudformation:us-west-2:738054984624:stack/eksctl-prototype-nodegroup-devops/0153cc00-dda6-11ea-b1af-066ac882f2e8</StackId>
        <StackName>eksctl-prototype-nodegroup-devops</StackName>
        <Description>EKS Managed Nodes (SSH access: true) [created by eksctl]</Description>
        <StackStatus>CREATE_COMPLETE</StackStatus>
        <DisableRollback>false</DisableRollback>
        <Tags>
          <member>
            <Value>prototype</Value>
            <Key>alpha.eksctl.io/cluster-name</Key>
          </member>
          <member>
            <Value>Infrastructure</Value>
            <Key>Owner</Key>
          </member>
          <member>
            <Value>devops</Value>
            <Key>alpha.eksctl.io/nodegroup-name</Key>
          </member>
          <member>
            <Value>prototype</Value>
            <Key>eksctl.cluster.k8s.io/v1alpha1/cluster-name</Key>
          </member>
          <member>
            <Value>DevOps Team</Value>
            <Key>Team</Key>
          </member>
          <member>
            <Value>managed</Value>
            <Key>alpha.eksctl.io/nodegroup-type</Key>
          </member>
          <member>
            <Value>Eduardo Valdes</Value>
            <Key>Creator</Key>
          </member>
          <member>
            <Value>0.25.0</Value>
            <Key>alpha.eksctl.io/eksctl-version</Key>
          </member>
        </Tags>
        <RollbackConfiguration/>
        <DriftInformation>
          <StackDriftStatus>NOT_CHECKED</StackDriftStatus>
        </DriftInformation>
        <EnableTerminationProtection>false</EnableTerminationProtection>
      </member>
    </Stacks>
  </DescribeStacksResult>
  <ResponseMetadata>
    <RequestId>e1f4c8e6-d7d1-472e-8c4c-f7092cc456e0</RequestId>
  </ResponseMetadata>
</DescribeStacksResponse>
```

```console
2020-08-13T13:49:19-07:00 [▶]  processing stack outputs
2020-08-13T13:49:19-07:00 [▶]  completed task: create managed nodegroup "devops"
2020-08-13T13:49:19-07:00 [▶]  completed task: create managed nodegroup "devops"
2020-08-13T13:49:19-07:00 [▶]  completed task: 2 sequential sub-tasks: { 2 sequential sub-tasks: { tag cluster, create fargate profiles }, create managed nodegroup "devops" }
2020-08-13T13:49:19-07:00 [ℹ]  waiting for the control plane availability...
2020-08-13T13:49:19-07:00 [▶]  merging kubeconfig files
2020-08-13T13:49:19-07:00 [▶]  setting current-context to eduardo.valdes@prototype.us-west-2.eksctl.io
2020-08-13T13:49:19-07:00 [✔]  saved kubeconfig as "/Users/emvaldes/.kube/eksctl/clusters/prototype"
2020-08-13T13:49:19-07:00 [ℹ]  no tasks
2020-08-13T13:49:19-07:00 [▶]  no actual tasks
2020-08-13T13:49:19-07:00 [✔]  all EKS cluster resources for "prototype" have been created
2020-08-13T13:49:19-07:00 [ℹ]  nodegroup "devops" has 2 node(s)
2020-08-13T13:49:19-07:00 [ℹ]  node "ip-192-168-47-189.us-west-2.compute.internal" is ready
2020-08-13T13:49:19-07:00 [ℹ]  node "ip-192-168-85-124.us-west-2.compute.internal" is ready
2020-08-13T13:49:19-07:00 [ℹ]  waiting for at least 2 node(s) to become ready in "devops"
2020-08-13T13:49:19-07:00 [ℹ]  nodegroup "devops" has 2 node(s)
2020-08-13T13:49:19-07:00 [ℹ]  node "ip-192-168-47-189.us-west-2.compute.internal" is ready
2020-08-13T13:49:19-07:00 [ℹ]  node "ip-192-168-85-124.us-west-2.compute.internal" is ready
2020-08-13T13:49:19-07:00 [▶]  kubectl: "/usr/local/bin/kubectl"
2020-08-13T13:49:20-07:00 [▶]  kubectl version: v1.18.6
2020-08-13T13:49:20-07:00 [▶]  found authenticator: aws-iam-authenticator
2020-08-13T13:49:23-07:00 [ℹ]  kubectl command should work with "/Users/emvaldes/.kube/eksctl/clusters/prototype", try 'kubectl --kubeconfig=/Users/emvaldes/.kube/eksctl/clusters/prototype get nodes'
2020-08-13T13:49:23-07:00 [✔]  EKS cluster "prototype" in "us-west-2" region is ready
2020-08-13T13:49:23-07:00 [▶]  cfg.json = \
```

```json
{
    "kind": "ClusterConfig",
    "apiVersion": "eksctl.io/v1alpha5",
    "metadata": {
        "name": "prototype",
        "region": "us-west-2",
        "version": "1.15",
        "tags": {
            "Creator": "Eduardo Valdes",
            "Owner": "Infrastructure",
            "Team": "DevOps Team"
        }
    },
    "iam": {
        "serviceRoleARN": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-11WWHVBHUS8SU",
        "fargatePodExecutionRoleARN": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
        "withOIDC": false
    },
    "vpc": {
        "id": "vpc-0fbc47be0823afa5c",
        "cidr": "192.168.0.0/16",
        "securityGroup": "sg-03333ef6a52a9493b",
        "subnets": {
            "private": {
                "us-west-2a": {
                    "id": "subnet-0c8745dead9e6ad94",
                    "cidr": "192.168.96.0/19"
                },
                "us-west-2b": {
                    "id": "subnet-01f0c768fca0cdd73",
                    "cidr": "192.168.128.0/19"
                },
                "us-west-2c": {
                    "id": "subnet-043a3e50cf9e9da34",
                    "cidr": "192.168.160.0/19"
                }
            },
            "public": {
                "us-west-2a": {
                    "id": "subnet-0788533b3af3ff72c",
                    "cidr": "192.168.0.0/19"
                },
                "us-west-2b": {
                    "id": "subnet-07a588c63b48da4e1",
                    "cidr": "192.168.32.0/19"
                },
                "us-west-2c": {
                    "id": "subnet-03399f59f0f174044",
                    "cidr": "192.168.64.0/19"
                }
            }
        },
        "sharedNodeSecurityGroup": "sg-07f40333322755358",
        "autoAllocateIPv6": false,
        "nat": {
            "gateway": "Disable"
        },
        "clusterEndpoints": {
            "privateAccess": false,
            "publicAccess": true
        }
    },
    "privateCluster": {
        "enabled": false
    },
    "managedNodeGroups": [
        {
            "name": "devops",
            "amiFamily": "AmazonLinux2",
            "instanceType": "m5.large",
            "desiredCapacity": 2,
            "minSize": 2,
            "maxSize": 3,
            "volumeSize": 80,
            "ssh": {
                "allow": true,
                "publicKeyPath": "/Users/emvaldes/.ssh/kubernetes.pub",
                "publicKeyName": "eksctl-prototype-nodegroup-devops-86:5e:92:83:18:fe:c1:25:04:cb:e2:00:2e:b8:6e:c0"
            },
            "labels": {
                "alpha.eksctl.io/cluster-name": "prototype",
                "alpha.eksctl.io/nodegroup-name": "devops"
            },
            "privateNetworking": false,
            "tags": {
                "alpha.eksctl.io/nodegroup-name": "devops",
                "alpha.eksctl.io/nodegroup-type": "managed"
            },
            "iam": {
                "withAddonPolicies": {
                    "imageBuilder": true,
                    "autoScaler": true,
                    "externalDNS": false,
                    "certManager": false,
                    "appMesh": true,
                    "appMeshPreview": false,
                    "ebs": false,
                    "fsx": false,
                    "efs": false,
                    "albIngress": true,
                    "xRay": false,
                    "cloudWatch": false
                }
            }
        }
    ],
    "fargateProfiles": [
        {
            "name": "fp-default",
            "podExecutionRoleARN": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-HCNSJF97FEAS",
            "selectors": [
                {
                    "namespace": "default"
                },
                {
                    "namespace": "kube-system"
                }
            ]
        }
    ],
    "availabilityZones": [
        "us-west-2a",
        "us-west-2b",
        "us-west-2c"
    ],
    "cloudWatch": {
        "clusterLogging": {}
    },
    "status": {
        "endpoint": "https://19099E1AA03B92443BA10641A6F620B7.gr7.us-west-2.eks.amazonaws.com",
        "certificateAuthorityData": "S0tLS1CRU ... UtLS0tLQo=",
        "arn": "arn:aws:eks:us-west-2:738054984624:cluster/prototype",
        "stackName": "eksctl-prototype-cluster"
    }
}
```

```console
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: DATA+OMITTED
    server: https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com
  name: prototype.us-east-1.eksctl.io
contexts:
- context:
    cluster: prototype.us-east-1.eksctl.io
    user: kubernetes@prototype.us-east-1.eksctl.io
  name: kubernetes@prototype.us-east-1.eksctl.io
current-context: kubernetes@prototype.us-east-1.eksctl.io
kind: Config
preferences: {}
users:
- name: kubernetes@prototype.us-east-1.eksctl.io
  user:
    exec:
      apiVersion: client.authentication.k8s.io/v1alpha1
      args:
      - token
      - -i
      - prototype
      command: aws-iam-authenticator
      env:
      - name: AWS_PROFILE
        value: kubernetes
```

```console
Function [cluster_token]:
{
    "apiVersion": "client.authentication.k8s.io/v1alpha1",
    "kind": "ExecCredential",
    "spec": {},
    "status": {
        "expirationTimestamp": "2019-12-23T08:57:47Z",
        "token": "k8s-aws-v1.aHR0cHM6Ly9zdHMuYW1hem9uYXdzLmNvbS8_QWN0aW9uPUdldENhbGxlcklkZW50aXR5JlZlcnNpb249MjAxMS0wNi0xNSZYLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFaWlAyNjU0MkJLQzI3TDRZJTJGMjAxOTEyMjMlMkZ1cy1lYXN0LTElMkZzdHMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDE5MTIyM1QwODQzNDdaJlgtQW16LUV4cGlyZXM9MCZYLUFtei1TaWduZWRIZWFkZXJzPWhvc3QlM0J4LWs4cy1hd3MtaWQmWC1BbXotU2lnbmF0dXJlPWM4NjI1NjU2MmM5YzRhYzk5YjJhMzBmMzFiMGQwMzExYzFmYzkyNjY5ZDYxZGIwZDVlODQ3ODAzYjMwZGJlZWQ"
    }
}
```

```console
Function [configure_logging]:
[ℹ]  eksctl version 0.11.1
[ℹ]  using region us-east-1
[ℹ]  will update CloudWatch logging for cluster "prototype" in "us-east-1" (enable types: api, audit, authenticator, controllerManager, scheduler & no types to disable)
[✔]  configured CloudWatch logging for cluster "prototype" in "us-east-1" (enabled types: api, audit, authenticator, controllerManager, scheduler & no types disabled)
```

```console
Function [metricsserver_deploy]:
clusterrole.rbac.authorization.k8s.io/system:aggregated-metrics-reader created
clusterrolebinding.rbac.authorization.k8s.io/metrics-server:system:auth-delegator created
rolebinding.rbac.authorization.k8s.io/metrics-server-auth-reader created
apiservice.apiregistration.k8s.io/v1beta1.metrics.k8s.io created
serviceaccount/metrics-server created
deployment.apps/metrics-server created
service/metrics-server created
clusterrole.rbac.authorization.k8s.io/system:metrics-server created
clusterrolebinding.rbac.authorization.k8s.io/system:metrics-server created
```

```console
Function [describe_stacks]:
[ℹ]  eksctl version 0.11.1
[ℹ]  using region us-east-1
[ℹ]  stack/eksctl-prototype-nodegroup-devops = {
  Capabilities: ["CAPABILITY_IAM"],
  CreationTime: 2019-12-23 08:41:16.73 +0000 UTC,
  Description: "EKS Managed Nodes (SSH access: true) [created by eksctl]",
  DisableRollback: false,
  DriftInformation: {
    StackDriftStatus: "NOT_CHECKED"
  },
  EnableTerminationProtection: false,
  RollbackConfiguration: {

  },
  StackId: "arn:aws:cloudformation:us-east-1:738054984624:stack/eksctl-prototype-nodegroup-devops/fbe8cbc0-255f-11ea-ae41-0afe492705d7",
  StackName: "eksctl-prototype-nodegroup-devops",
  StackStatus: "CREATE_COMPLETE",
  Tags: [
    {
      Key: "alpha.eksctl.io/cluster-name",
      Value: "prototype"
    },
    {
      Key: "Owner",
      Value: "SRE Team"
    },
    {
      Key: "alpha.eksctl.io/nodegroup-name",
      Value: "devops"
    },
    {
      Key: "eksctl.cluster.k8s.io/v1alpha1/cluster-name",
      Value: "prototype"
    },
    {
      Key: "Team",
      Value: "DevOps Team"
    },
    {
      Key: "alpha.eksctl.io/nodegroup-type",
      Value: "managed"
    },
    {
      Key: "Creator",
      Value: "Eduardo Valdes"
    }
  ]
}
[ℹ]  stack/eksctl-prototype-cluster = {
  Capabilities: ["CAPABILITY_IAM"],
  CreationTime: 2019-12-23 08:28:34.88 +0000 UTC,
  Description: "EKS cluster (dedicated VPC: true, dedicated IAM: true) [created and managed by eksctl]",
  DisableRollback: false,
  DriftInformation: {
    StackDriftStatus: "NOT_CHECKED"
  },
  EnableTerminationProtection: false,
  Outputs: [
    {
      ExportName: "eksctl-prototype-cluster::SubnetsPrivate",
      OutputKey: "SubnetsPrivate",
      OutputValue: "subnet-06f80d112a35bcbc5,subnet-088cf0f3c3ca8d8a3,subnet-03804f05568eb39ba"
    },
    {
      ExportName: "eksctl-prototype-cluster::SubnetsPublic",
      OutputKey: "SubnetsPublic",
      OutputValue: "subnet-0f5f396fc169fa3cc,subnet-09a7c44bb0d763ea1,subnet-0f2ee3e2b65f9660f"
    },
    {
      ExportName: "eksctl-prototype-cluster::ServiceRoleARN",
      OutputKey: "ServiceRoleARN",
      OutputValue: "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-1NTUNUAY288AO"
    },
    {
      ExportName: "eksctl-prototype-cluster::VPC",
      OutputKey: "VPC",
      OutputValue: "vpc-094eb6f95cb478207"
    },
    {
      OutputKey: "ClusterStackName",
      OutputValue: "eksctl-prototype-cluster"
    },
    {
      OutputKey: "CertificateAuthorityData",
      OutputValue: "LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUN5RENDQWJDZ0F3SUJBZ0lCQURBTkJna3Foa2lHOXcwQkFRc0ZBREFWTVJNd0VRWURWUVFERXdwcmRXSmwKY201bGRHVnpNQjRYRFRFNU1USXlNekE0TXpneU9Wb1hEVEk1TVRJeU1EQTRNemd5T1Zvd0ZURVRNQkVHQTFVRQpBeE1LYTNWaVpYSnVaWFJsY3pDQ0FTSXdEUVlKS29aSWh2Y05BUUVCQlFBRGdnRVBBRENDQVFvQ2dnRUJBS21RCmJFRmZkTEdTSUU5YTgzY3ZIMFBqblJOZEo3aHN2VDV2UlpLcFlOZlg3TWdiZ0hVOG11WXdJYnZVQjJDSXZNK3kKN2M2QVozeUsrSTd5WjIxck5kSlBsaFV5RThZd09RdGJxOGNDdHl2RklFUnRxRXVrbmo2MW1ET01LTXFjeDdpQgpySTdHWVFrbmtYME83VUdhQWRpOExIaXBCTXdpTHI5bEhHQXhQSGx6V3pJcTdEUXNBc0VnaW9CTHhNVUtOaFRwCmljeFFIOVU2MXdtZGFIeXJ3WFRubm4vWGRBdUtmWVRmOWZzczlXa2ZDTTdCdmZzNjUxaUh5WVFsaDJJNjJCcTAKWWFDNUt1ODFkam4rZXVZak1TTFg1QlJrZTdDMFBqeHgzT0huek52R2lzVGNxcHNjZktuWVRRWStpT0IzNDh6SwpKYzRnYkNNWFl1djhUalB1bTVjQ0F3RUFBYU1qTUNFd0RnWURWUjBQQVFIL0JBUURBZ0trTUE4R0ExVWRFd0VCCi93UUZNQU1CQWY4d0RRWUpLb1pJaHZjTkFRRUxCUUFEZ2dFQkFIZ3RsSk9zTWkraWZST1RMWERrLzhwbksyOHIKNGdvWFpCTXNoaVpKYXhWMWo1WURTSUc5dzZlNUUyZlQ3d05Ud0ZLWWk2MXNodERIK1NLaGRRaFBtN1FaLy9EOAphaGRORnNpTkdYVHhMVzhPSlNXa1graWZXWStKS3AzWWVlWkN1bDFYd3lkc0xsMGJSYldaNVBEdk9VQW1jNng3CmcyZEMyekxBaklRdU1KbHdjWGFEYmF6UzRra1VSVkpWZFNpUW5tOW5nZmttWDZrSmtJeDJENmZjV0FSeUFZVGgKVGJsWFFoMGY5L2YweDdIUHNvOFBWeDJXV1JRbnZoanlnVVlOK3BUNEduTm9DZkliVHBVS2pOQjJsMkpjNElZawpUVmhKSHlSaVNzSWZLL1J5T0F0RWxvckRqU0N4YXFmV2tVU0pYZXFjM2IvVkJIa1RVeVhvRElwTEVYTT0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo="
    },
    {
      ExportName: "eksctl-prototype-cluster::SecurityGroup",
      OutputKey: "SecurityGroup",
      OutputValue: "sg-054594ae12482ff56"
    },
    {
      OutputKey: "FeatureNATMode",
      OutputValue: "Single"
    },
    {
      ExportName: "eksctl-prototype-cluster::Endpoint",
      OutputKey: "Endpoint",
      OutputValue: "https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com"
    },
    {
      ExportName: "eksctl-prototype-cluster::SharedNodeSecurityGroup",
      OutputKey: "SharedNodeSecurityGroup",
      OutputValue: "sg-0992e20edb053545d"
    },
    {
      ExportName: "eksctl-prototype-cluster::ClusterSecurityGroupId",
      OutputKey: "ClusterSecurityGroupId",
      OutputValue: "sg-0802d870efe4f66a2"
    },
    {
      ExportName: "eksctl-prototype-cluster::ARN",
      OutputKey: "ARN",
      OutputValue: "arn:aws:eks:us-east-1:738054984624:cluster/prototype"
    },
    {
      ExportName: "eksctl-prototype-cluster::FargatePodExecutionRoleARN",
      OutputKey: "FargatePodExecutionRoleARN",
      OutputValue: "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-FargatePodExecutionRole-ZUY6UD2QGJSV"
    }
  ],
  RollbackConfiguration: {

  },
  StackId: "arn:aws:cloudformation:us-east-1:738054984624:stack/eksctl-prototype-cluster/35ae2460-255e-11ea-b30f-0a4f04019892",
  StackName: "eksctl-prototype-cluster",
  StackStatus: "CREATE_COMPLETE",
  Tags: [
    {
      Key: "alpha.eksctl.io/cluster-name",
      Value: "prototype"
    },
    {
      Key: "Owner",
      Value: "SRE Team"
    },
    {
      Key: "eksctl.cluster.k8s.io/v1alpha1/cluster-name",
      Value: "prototype"
    },
    {
      Key: "Team",
      Value: "DevOps Team"
    },
    {
      Key: "Creator",
      Value: "Eduardo Valdes"
    }
  ]
}
```

```console
Function [display_nodes]:

NAME                             STATUS   ROLES    AGE    VERSION              INTERNAL-IP      EXTERNAL-IP    OS-IMAGE         KERNEL-VERSION                  CONTAINER-RUNTIME
ip-192-168-52-90.ec2.internal    Ready    <none>   106s   v1.14.7-eks-1861c5   192.168.52.90    3.82.219.54    Amazon Linux 2   4.14.146-119.123.amzn2.x86_64   docker://18.6.1
ip-192-168-66-209.ec2.internal   Ready    <none>   2m1s   v1.14.7-eks-1861c5   192.168.66.209   3.87.238.174   Amazon Linux 2   4.14.146-119.123.amzn2.x86_64   docker://18.6.1
```

```console
Function [create_autoscaler]:
serviceaccount/cluster-autoscaler created
clusterrole.rbac.authorization.k8s.io/cluster-autoscaler created
role.rbac.authorization.k8s.io/cluster-autoscaler created
clusterrolebinding.rbac.authorization.k8s.io/cluster-autoscaler created
rolebinding.rbac.authorization.k8s.io/cluster-autoscaler created
deployment.apps/cluster-autoscaler created
```

```console
Function [autoscaler_group]:
Auto-Scaling Group Name: eks-9cb798f5-9fda-4fbf-09e1-e1773d132961
```

```console
Function [disable_eviction]:
deployment.apps/cluster-autoscaler annotated
```

```console
Function [autoscaler_version]:
deployment.apps/cluster-autoscaler image updated
```

```console
Function [autoscaler_update]:

Modify these lines:
- --node-group-auto-discovery=asg:tag=k8s.io/cluster-autoscaler/enabled,k8s.io/cluster-autoscaler/prototype

Append these lines:
- --balance-similar-node-groups
- --skip-nodes-with-system-pods=false
deployment.apps/cluster-autoscaler edited
```

```console
Function [inspect_autoscaler]:
```

```console
Function [configmap_awsauth]:
/tmp/devops/prototype/aws-auth-cm.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: aws-auth
  namespace: kube-system
data:
  mapRoles: |
    - rolearn: arn:aws:iam::738054984624:role/eksctl-prototype-nodegroup-devops-NodeInstanceRole-EAECB0XT8T2L
      username: system:node:{{EC2PrivateDNSName}}
      groups:
        - system:bootstrappers
        - system:nodes
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
configmap/aws-auth configured
Name:         aws-auth
Namespace:    kube-system
Labels:       <none>
Annotations:  kubectl.kubernetes.io/last-applied-configuration:
                {"apiVersion":"v1","data":{"mapRoles":"- rolearn: arn:aws:iam::738054984624:role/eksctl-prototype-nodegroup-devops-NodeInstanceRole-EAECB0XT...

Data
====
mapRoles:
----
- rolearn: arn:aws:iam::738054984624:role/eksctl-prototype-nodegroup-devops-NodeInstanceRole-EAECB0XT8T2L
  username: system:node:{{EC2PrivateDNSName}}
  groups:
    - system:bootstrappers
    - system:nodes

Events:  <none>
```

```console
Function [metricshelper_deploy]:
clusterrole.rbac.authorization.k8s.io/cni-metrics-helper created
serviceaccount/cni-metrics-helper created
clusterrolebinding.rbac.authorization.k8s.io/cni-metrics-helper created
deployment.extensions/cni-metrics-helper created
```

```console
Function [metricshelper_policy]:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "cloudwatch:PutMetricData",
      "Resource": "*"
    }
  ]
}

An error occurred (EntityAlreadyExists) when calling the CreatePolicy operation: A policy called CNIMetricsHelperPolicy--prototype-devops already exists. Duplicate names are not allowed.
```

```console
Function [metricshelper_rolepolicies]:
```

```console
Function [instance_roleupdate]:
{
    "IamInstanceProfileAssociation": {
        "AssociationId": "iip-assoc-010afe541671c251e",
        "InstanceId": "i-034c200337e766387",
        "IamInstanceProfile": {
            "Arn": "arn:aws:iam::738054984624:instance-profile/eks-9cb798f5-9fda-4fbf-09e1-e1773d132961",
            "Id": "AIPAZZP26542MDVOITYAD"
        },
        "State": "associated"
    }
}
{
    "IamInstanceProfileAssociation": {
        "AssociationId": "iip-assoc-044c76b85b2cf39d0",
        "InstanceId": "i-074e0f0d3ab1e6dab",
        "IamInstanceProfile": {
            "Arn": "arn:aws:iam::738054984624:instance-profile/eks-9cb798f5-9fda-4fbf-09e1-e1773d132961",
            "Id": "AIPAZZP26542MDVOITYAD"
        },
        "State": "associated"
    }
}
```

```console
Function [cloudwatch_namespace]:
namespace/amazon-cloudwatch created
```

```console
Function [cwagent_fluentd]:
namespace/amazon-cloudwatch unchanged
serviceaccount/cloudwatch-agent created
clusterrole.rbac.authorization.k8s.io/cloudwatch-agent-role created
clusterrolebinding.rbac.authorization.k8s.io/cloudwatch-agent-role-binding created
configmap/cwagentconfig created
daemonset.apps/cloudwatch-agent created
configmap/cluster-info created
serviceaccount/fluentd created
clusterrole.rbac.authorization.k8s.io/fluentd-role created
clusterrolebinding.rbac.authorization.k8s.io/fluentd-role-binding created
configmap/fluentd-config created
daemonset.apps/fluentd-cloudwatch created
```

```console
Function [display_pods]: amazon-cloudwatch
NAME                       READY   STATUS              RESTARTS   AGE   IP       NODE                             NOMINATED NODE   READINESS GATES
cloudwatch-agent-t6nxd     0/1     ContainerCreating   0          2s    <none>   ip-192-168-52-90.ec2.internal    <none>           <none>
fluentd-cloudwatch-kx4k4   0/1     Init:0/2            0          1s    <none>   ip-192-168-52-90.ec2.internal    <none>           <none>
cloudwatch-agent-k2pqs     0/1     ContainerCreating   0          2s    <none>   ip-192-168-66-209.ec2.internal   <none>           <none>
fluentd-cloudwatch-p5t8x   0/1     Init:0/2            0          1s    <none>   ip-192-168-66-209.ec2.internal   <none>           <none>
```

```console
Function [cwagent_serviceaccount]:
serviceaccount/cloudwatch-agent unchanged
clusterrole.rbac.authorization.k8s.io/cloudwatch-agent-role unchanged
clusterrolebinding.rbac.authorization.k8s.io/cloudwatch-agent-role-binding unchanged
```

```console
Function [configmap_cwagent]:
/tmp/devops/prototype/cwagent-configmap.yaml
configmap/cwagentconfig configured
```

```console
Function [cwagent_daemonset]:
daemonset.apps/cloudwatch-agent unchanged
```

```console
Function [cluster_podname]: amazon-cloudwatch
```

```console
Describing Pod: cloudwatch-agent-k2pqs

Function [describe_podname]: cloudwatch-agent-k2pqs
Name:           cloudwatch-agent-k2pqs
Namespace:      amazon-cloudwatch
Priority:       0
Node:           ip-192-168-66-209.ec2.internal/192.168.66.209
Start Time:     Mon, 23 Dec 2019 01:46:12 -0700
Labels:         controller-revision-hash=7cb45c7f8c
                name=cloudwatch-agent
                pod-template-generation=1
Annotations:    kubernetes.io/psp: eks.privileged
Status:         Running
IP:             192.168.65.184
IPs:            <none>
Controlled By:  DaemonSet/cloudwatch-agent
Containers:
  cloudwatch-agent:
    Container ID:   docker://ddd8e75d6f1cbc17f6c7a7eaad9b16fb148883139f1c5a38b072842d1fd171a9
    Image:          amazon/cloudwatch-agent:1.230621.0
    Image ID:       docker-pullable://amazon/cloudwatch-agent@sha256:877106acbc56e747ebe373548c88cd37274f666ca11b5c782211db4c5c7fb64b
    Port:           <none>
    Host Port:      <none>
    State:          Running
      Started:      Mon, 23 Dec 2019 01:46:15 -0700
    Ready:          True
    Restart Count:  0
    Limits:
      cpu:     200m
      memory:  200Mi
    Requests:
      cpu:     200m
      memory:  200Mi
    Environment:
      HOST_IP:         (v1:status.hostIP)
      HOST_NAME:       (v1:spec.nodeName)
      K8S_NAMESPACE:  amazon-cloudwatch (v1:metadata.namespace)
      CI_VERSION:     k8s/1.0.1
    Mounts:
      /dev/disk from devdisk (ro)
      /etc/cwagentconfig from cwagentconfig (rw)
      /rootfs from rootfs (ro)
      /sys from sys (ro)
      /var/lib/docker from varlibdocker (ro)
      /var/run/docker.sock from dockersock (ro)
      /var/run/secrets/kubernetes.io/serviceaccount from cloudwatch-agent-token-q2l8q (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  cwagentconfig:
    Type:      ConfigMap (a volume populated by a ConfigMap)
    Name:      cwagentconfig
    Optional:  false
  rootfs:
    Type:          HostPath (bare host directory volume)
    Path:          /
    HostPathType:
  dockersock:
    Type:          HostPath (bare host directory volume)
    Path:          /var/run/docker.sock
    HostPathType:
  varlibdocker:
    Type:          HostPath (bare host directory volume)
    Path:          /var/lib/docker
    HostPathType:
  sys:
    Type:          HostPath (bare host directory volume)
    Path:          /sys
    HostPathType:
  devdisk:
    Type:          HostPath (bare host directory volume)
    Path:          /dev/disk/
    HostPathType:
  cloudwatch-agent-token-q2l8q:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  cloudwatch-agent-token-q2l8q
    Optional:    false
QoS Class:       Guaranteed
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/disk-pressure:NoSchedule
                 node.kubernetes.io/memory-pressure:NoSchedule
                 node.kubernetes.io/not-ready:NoExecute
                 node.kubernetes.io/pid-pressure:NoSchedule
                 node.kubernetes.io/unreachable:NoExecute
                 node.kubernetes.io/unschedulable:NoSchedule
Events:
  Type    Reason     Age   From                                     Message
  ----    ------     ----  ----                                     -------
  Normal  Scheduled  6s    default-scheduler                        Successfully assigned amazon-cloudwatch/cloudwatch-agent-k2pqs to ip-192-168-66-209.ec2.internal
  Normal  Pulling    5s    kubelet, ip-192-168-66-209.ec2.internal  Pulling image "amazon/cloudwatch-agent:1.230621.0"
  Normal  Pulled     3s    kubelet, ip-192-168-66-209.ec2.internal  Successfully pulled image "amazon/cloudwatch-agent:1.230621.0"
  Normal  Created    3s    kubelet, ip-192-168-66-209.ec2.internal  Created container cloudwatch-agent
  Normal  Started    3s    kubelet, ip-192-168-66-209.ec2.internal  Started container cloudwatch-agent
```

```console
Displaying Pod's Log: cloudwatch-agent-k2pqs

2019/12/23 08:46:15 I! I! Detected the instance is EC2
2019/12/23 08:46:15 Reading json config file path: /opt/aws/amazon-cloudwatch-agent/bin/default_linux_config.json ...
/opt/aws/amazon-cloudwatch-agent/bin/default_linux_config.json does not exist or cannot read. Skipping it.
2019/12/23 08:46:15 Reading json config file path: /etc/cwagentconfig/..2019_12_23_08_46_12.683569077/cwagentconfig.json ...
2019/12/23 08:46:15 Find symbolic link /etc/cwagentconfig/..data
2019/12/23 08:46:15 Find symbolic link /etc/cwagentconfig/cwagentconfig.json
2019/12/23 08:46:15 Reading json config file path: /etc/cwagentconfig/cwagentconfig.json ...
Valid Json input schema.
No csm configuration found.
No metric configuration found.
Configuration validation first phase succeeded

2019/12/23 08:46:15 I! Config has been translated into TOML /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.toml
2019/12/23 08:46:15 I! AmazonCloudWatchAgent Version 1.230621.0.
2019-12-23T08:46:15Z I! Starting AmazonCloudWatchAgent (version 1.230621.0)
2019-12-23T08:46:15Z I! Loaded outputs: cloudwatchlogs
2019-12-23T08:46:15Z I! Loaded inputs: cadvisor k8sapiserver
2019-12-23T08:46:15Z I! Tags enabled:
2019-12-23T08:46:15Z I! Agent Config: Interval:1m0s, Quiet:false, Hostname:"ip-192-168-66-209.ec2.internal", Flush Interval:1s
2019-12-23T08:46:15Z I! Cannot get the leader config map: configmaps "cwagent-clusterleader" not found, try to create the config map...
2019-12-23T08:46:15Z I! configMap: &ConfigMap{ObjectMeta:k8s_io_apimachinery_pkg_apis_meta_v1.ObjectMeta{Name:cwagent-clusterleader,GenerateName:,Namespace:amazon-cloudwatch,SelfLink:/api/v1/namespaces/amazon-cloudwatch/configmaps/cwagent-clusterleader,UID:ae416aad-2560-11ea-83e0-0a20636a20d3,ResourceVersion:1342,Generation:0,CreationTimestamp:2019-12-23 08:46:15 +0000 UTC,DeletionTimestamp:<nil>,DeletionGracePeriodSeconds:nil,Labels:map[string]string{},Annotations:map[string]string{},OwnerReferences:[],Finalizers:[],ClusterName:,Initializers:nil,},Data:map[string]string{},BinaryData:map[string][]byte{},}, err: <nil>
2019-12-23T08:46:15Z I! k8sapiserver OnStartedLeading: ip-192-168-66-209.ec2.internal
```

```console
Function [create_namespace]: prometheus
namespace/prometheus created
```

```console
Function [service_account]: tiller
apiVersion: v1
kind: ServiceAccount
metadata:
  name: tiller
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: tiller
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
  - kind: ServiceAccount
    name: tiller
    namespace: kube-system

serviceaccount/tiller created
clusterrolebinding.rbac.authorization.k8s.io/tiller created
$HELM_HOME has been configured at /Users/prototype/.helm.

Tiller (the Helm server-side component) has been installed into your Kubernetes Cluster.

Please note: by default, Tiller is deployed with an insecure 'allow unauthenticated users' policy.
To prevent this, run `helm init` with the --tiller-tls-verify flag.
For more information on securing your installation see: https://docs.helm.sh/using_helm/#securing-your-helm-installation

NAME            READY   UP-TO-DATE   AVAILABLE   AGE
tiller-deploy   1/1     1            1           61s

Name:                   tiller-deploy
Namespace:              kube-system
CreationTimestamp:      Mon, 23 Dec 2019 01:46:35 -0700
Labels:                 app=helm
                        name=tiller
Annotations:            deployment.kubernetes.io/revision: 1
Selector:               app=helm,name=tiller
Replicas:               1 desired | 1 updated | 1 total | 1 available | 0 unavailable
StrategyType:           RollingUpdate
MinReadySeconds:        0
RollingUpdateStrategy:  25% max unavailable, 25% max surge
Pod Template:
  Labels:           app=helm
                    name=tiller
  Service Account:  tiller
  Containers:
   tiller:
    Image:       gcr.io/kubernetes-helm/tiller:v2.16.1
    Ports:       44134/TCP, 44135/TCP
    Host Ports:  0/TCP, 0/TCP
    Liveness:    http-get http://:44135/liveness delay=1s timeout=1s period=10s #success=1 #failure=3
    Readiness:   http-get http://:44135/readiness delay=1s timeout=1s period=10s #success=1 #failure=3
    Environment:
      TILLER_NAMESPACE:    kube-system
      TILLER_HISTORY_MAX:  300
    Mounts:                <none>
  Volumes:                 <none>
Conditions:
  Type           Status  Reason
  ----           ------  ------
  Available      True    MinimumReplicasAvailable
  Progressing    True    NewReplicaSetAvailable
OldReplicaSets:  <none>
NewReplicaSet:   tiller-deploy-54c98f988f (1/1 replicas created)
Events:
  Type    Reason             Age   From                   Message
  ----    ------             ----  ----                   -------
  Normal  ScalingReplicaSet  61s   deployment-controller  Scaled up replica set tiller-deploy-54c98f988f to 1
```

```console
Function [setup_monitoring]: prometheus
2019/12/23 01:47:38 Warning: Merging destination map for chart 'prometheus-node-exporter'. Overwriting table item 'extraArgs', with non table value: [--collector.filesystem.ignored-mount-points=^/(dev|proc|sys|var/lib/docker/.+)($|/) --collector.filesystem.ignored-fs-types=^(autofs|binfmt_misc|cgroup|configfs|debugfs|devpts|devtmpfs|fusectl|hugetlbfs|mqueue|overlay|proc|procfs|pstore|rpc_pipefs|securityfs|sysfs|tracefs)$]
2019/12/23 01:47:38 Warning: Merging destination map for chart 'prometheus-node-exporter'. Overwriting table item 'extraArgs', with non table value: [--collector.filesystem.ignored-mount-points=^/(dev|proc|sys|var/lib/docker/.+)($|/) --collector.filesystem.ignored-fs-types=^(autofs|binfmt_misc|cgroup|configfs|debugfs|devpts|devtmpfs|fusectl|hugetlbfs|mqueue|overlay|proc|procfs|pstore|rpc_pipefs|securityfs|sysfs|tracefs)$]
NAME:   prometheus
LAST DEPLOYED: Mon Dec 23 01:47:40 2019
NAMESPACE: prometheus
STATUS: DEPLOYED

RESOURCES:
==> v1/Alertmanager
NAME                                     AGE
prometheus-prometheus-oper-alertmanager  34s

==> v1/ClusterRole
NAME                                       AGE
prometheus-grafana-clusterrole             34s
prometheus-prometheus-oper-alertmanager    34s
prometheus-prometheus-oper-operator        34s
prometheus-prometheus-oper-operator-psp    34s
prometheus-prometheus-oper-prometheus      34s
prometheus-prometheus-oper-prometheus-psp  34s
psp-prometheus-kube-state-metrics          34s

==> v1/ClusterRoleBinding
NAME                                       AGE
prometheus-grafana-clusterrolebinding      34s
prometheus-prometheus-oper-alertmanager    34s
prometheus-prometheus-oper-operator        34s
prometheus-prometheus-oper-operator-psp    34s
prometheus-prometheus-oper-prometheus      34s
prometheus-prometheus-oper-prometheus-psp  34s
psp-prometheus-kube-state-metrics          34s

==> v1/ConfigMap
NAME                                                          AGE
prometheus-grafana                                            34s
prometheus-grafana-config-dashboards                          34s
prometheus-grafana-test                                       34s
prometheus-prometheus-oper-apiserver                          34s
prometheus-prometheus-oper-controller-manager                 34s
prometheus-prometheus-oper-etcd                               34s
prometheus-prometheus-oper-grafana-datasource                 34s
prometheus-prometheus-oper-k8s-resources-cluster              34s
prometheus-prometheus-oper-k8s-resources-namespace            34s
prometheus-prometheus-oper-k8s-resources-pod                  34s
prometheus-prometheus-oper-k8s-resources-workload             34s
prometheus-prometheus-oper-k8s-resources-workloads-namespace  34s
prometheus-prometheus-oper-kubelet                            34s
prometheus-prometheus-oper-node-cluster-rsrc-use              34s
prometheus-prometheus-oper-node-rsrc-use                      34s
prometheus-prometheus-oper-nodes                              34s
prometheus-prometheus-oper-persistentvolumesusage             34s
prometheus-prometheus-oper-pods                               34s
prometheus-prometheus-oper-prometheus                         34s
prometheus-prometheus-oper-prometheus-remote-write            34s
prometheus-prometheus-oper-proxy                              34s
prometheus-prometheus-oper-scheduler                          34s
prometheus-prometheus-oper-statefulset                        34s

==> v1/Deployment
NAME                                 AGE
prometheus-grafana                   34s
prometheus-kube-state-metrics        34s
prometheus-prometheus-oper-operator  34s

==> v1/Pod(related)
NAME                                                  AGE
prometheus-grafana-5c97446694-9bhc7                   34s
prometheus-kube-state-metrics-5ffdf76ddd-f8pgx        34s
prometheus-prometheus-node-exporter-9nbsp             34s
prometheus-prometheus-node-exporter-cnxtz             34s
prometheus-prometheus-oper-operator-6d59dcfb57-2crvb  34s

==> v1/Prometheus
NAME                                   AGE
prometheus-prometheus-oper-prometheus  34s

==> v1/PrometheusRule
NAME                                                             AGE
prometheus-prometheus-oper-alertmanager.rules                    34s
prometheus-prometheus-oper-etcd                                  34s
prometheus-prometheus-oper-general.rules                         34s
prometheus-prometheus-oper-k8s.rules                             34s
prometheus-prometheus-oper-kube-apiserver.rules                  34s
prometheus-prometheus-oper-kube-prometheus-node-recording.rules  34s
prometheus-prometheus-oper-kube-scheduler.rules                  34s
prometheus-prometheus-oper-kubernetes-absent                     34s
prometheus-prometheus-oper-kubernetes-apps                       34s
prometheus-prometheus-oper-kubernetes-resources                  34s
prometheus-prometheus-oper-kubernetes-storage                    34s
prometheus-prometheus-oper-kubernetes-system                     34s
prometheus-prometheus-oper-node-exporter                         34s
prometheus-prometheus-oper-node-exporter.rules                   34s
prometheus-prometheus-oper-node-network                          34s
prometheus-prometheus-oper-node-time                             34s
prometheus-prometheus-oper-node.rules                            34s
prometheus-prometheus-oper-prometheus                            34s
prometheus-prometheus-oper-prometheus-operator                   34s

==> v1/Role
NAME                     AGE
prometheus-grafana-test  34s

==> v1/RoleBinding
NAME                     AGE
prometheus-grafana-test  34s

==> v1/Secret
NAME                                                  AGE
alertmanager-prometheus-prometheus-oper-alertmanager  34s
prometheus-grafana                                    34s

==> v1/Service
NAME                                                AGE
prometheus-grafana                                  34s
prometheus-kube-state-metrics                       34s
prometheus-prometheus-node-exporter                 34s
prometheus-prometheus-oper-alertmanager             34s
prometheus-prometheus-oper-coredns                  34s
prometheus-prometheus-oper-kube-controller-manager  34s
prometheus-prometheus-oper-kube-etcd                34s
prometheus-prometheus-oper-kube-proxy               34s
prometheus-prometheus-oper-kube-scheduler           34s
prometheus-prometheus-oper-operator                 34s
prometheus-prometheus-oper-prometheus               34s

==> v1/ServiceAccount
NAME                                     AGE
prometheus-grafana                       34s
prometheus-grafana-test                  34s
prometheus-kube-state-metrics            34s
prometheus-prometheus-node-exporter      34s
prometheus-prometheus-oper-alertmanager  34s
prometheus-prometheus-oper-operator      34s
prometheus-prometheus-oper-prometheus    34s

==> v1/ServiceMonitor
NAME                                                AGE
prometheus-prometheus-oper-alertmanager             34s
prometheus-prometheus-oper-apiserver                34s
prometheus-prometheus-oper-coredns                  34s
prometheus-prometheus-oper-grafana                  34s
prometheus-prometheus-oper-kube-controller-manager  34s
prometheus-prometheus-oper-kube-etcd                34s
prometheus-prometheus-oper-kube-proxy               34s
prometheus-prometheus-oper-kube-scheduler           34s
prometheus-prometheus-oper-kube-state-metrics       34s
prometheus-prometheus-oper-kubelet                  34s
prometheus-prometheus-oper-node-exporter            34s
prometheus-prometheus-oper-operator                 34s
prometheus-prometheus-oper-prometheus               34s

==> v1beta1/ClusterRole
NAME                                     AGE
prometheus-kube-state-metrics            34s
psp-prometheus-prometheus-node-exporter  34s

==> v1beta1/ClusterRoleBinding
NAME                                     AGE
prometheus-kube-state-metrics            34s
psp-prometheus-prometheus-node-exporter  34s

==> v1beta1/DaemonSet
NAME                                 AGE
prometheus-prometheus-node-exporter  34s

==> v1beta1/MutatingWebhookConfiguration
NAME                                  AGE
prometheus-prometheus-oper-admission  34s

==> v1beta1/PodSecurityPolicy
NAME                                     AGE
prometheus-grafana                       34s
prometheus-grafana-test                  34s
prometheus-kube-state-metrics            34s
prometheus-prometheus-node-exporter      34s
prometheus-prometheus-oper-alertmanager  34s
prometheus-prometheus-oper-operator      34s
prometheus-prometheus-oper-prometheus    34s

==> v1beta1/Role
NAME                AGE
prometheus-grafana  34s

==> v1beta1/RoleBinding
NAME                AGE
prometheus-grafana  34s

==> v1beta1/ValidatingWebhookConfiguration
NAME                                  AGE
prometheus-prometheus-oper-admission  34s


NOTES:
The Prometheus Operator has been installed. Check its status by running:
  kubectl --namespace prometheus get pods -l "release=prometheus"

Visit https://github.com/coreos/prometheus-operator for instructions on how
to create & configure Alertmanager and Prometheus instances using the Operator.

NAME                                                   READY   STATUS    RESTARTS   AGE
prometheus-grafana-5c97446694-9bhc7                    2/2     Running   0          2m34s
prometheus-prometheus-node-exporter-9nbsp              1/1     Running   0          2m34s
prometheus-prometheus-node-exporter-cnxtz              1/1     Running   0          2m34s
prometheus-prometheus-oper-operator-6d59dcfb57-2crvb   2/2     Running   0          2m34s
```

```console
Function [monitoring_services]:
{
    "apiVersion": "v1",
    "items": [
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:24Z",
                "labels": {
                    "operated-alertmanager": "true"
                },
                "name": "alertmanager-operated",
                "namespace": "prometheus",
                "ownerReferences": [
                    {
                        "apiVersion": "monitoring.coreos.com/v1",
                        "kind": "Alertmanager",
                        "name": "prometheus-prometheus-oper-alertmanager",
                        "uid": "f78a4893-2560-11ea-83e0-0a20636a20d3"
                    }
                ],
                "resourceVersion": "2013",
                "selfLink": "/api/v1/namespaces/prometheus/services/alertmanager-operated",
                "uid": "fb14a3bd-2560-11ea-a71a-02287af92a37"
            },
            "spec": {
                "clusterIP": "None",
                "ports": [
                    {
                        "name": "web",
                        "port": 9093,
                        "protocol": "TCP",
                        "targetPort": 9093
                    },
                    {
                        "name": "mesh-tcp",
                        "port": 9094,
                        "protocol": "TCP",
                        "targetPort": 9094
                    },
                    {
                        "name": "mesh-udp",
                        "port": 9094,
                        "protocol": "UDP",
                        "targetPort": 9094
                    }
                ],
                "selector": {
                    "app": "alertmanager"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app": "grafana",
                    "chart": "grafana-3.8.19",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "name": "prometheus-grafana",
                "namespace": "prometheus",
                "resourceVersion": "1866",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-grafana",
                "uid": "f783a5ef-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.200.160",
                "ports": [
                    {
                        "name": "service",
                        "port": 80,
                        "protocol": "TCP",
                        "targetPort": 3000
                    }
                ],
                "selector": {
                    "app": "grafana",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "annotations": {
                    "prometheus.io/scrape": "true"
                },
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app.kubernetes.io/instance": "prometheus",
                    "app.kubernetes.io/managed-by": "Tiller",
                    "app.kubernetes.io/name": "kube-state-metrics",
                    "helm.sh/chart": "kube-state-metrics-2.3.1"
                },
                "name": "prometheus-kube-state-metrics",
                "namespace": "prometheus",
                "resourceVersion": "1860",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-kube-state-metrics",
                "uid": "f781b42d-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.234.122",
                "ports": [
                    {
                        "name": "http",
                        "port": 8080,
                        "protocol": "TCP",
                        "targetPort": 8080
                    }
                ],
                "selector": {
                    "app.kubernetes.io/instance": "prometheus",
                    "app.kubernetes.io/name": "kube-state-metrics"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:34Z",
                "labels": {
                    "operated-prometheus": "true"
                },
                "name": "prometheus-operated",
                "namespace": "prometheus",
                "ownerReferences": [
                    {
                        "apiVersion": "monitoring.coreos.com/v1",
                        "kind": "Prometheus",
                        "name": "prometheus-prometheus-oper-prometheus",
                        "uid": "f7983943-2560-11ea-83e0-0a20636a20d3"
                    }
                ],
                "resourceVersion": "2095",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-operated",
                "uid": "00f067cb-2561-11ea-a71a-02287af92a37"
            },
            "spec": {
                "clusterIP": "None",
                "ports": [
                    {
                        "name": "web",
                        "port": 9090,
                        "protocol": "TCP",
                        "targetPort": "web"
                    }
                ],
                "selector": {
                    "app": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "annotations": {
                    "prometheus.io/scrape": "true"
                },
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app": "prometheus-node-exporter",
                    "chart": "prometheus-node-exporter-1.5.2",
                    "heritage": "Tiller",
                    "jobLabel": "node-exporter",
                    "release": "prometheus"
                },
                "name": "prometheus-prometheus-node-exporter",
                "namespace": "prometheus",
                "resourceVersion": "1854",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-node-exporter",
                "uid": "f78066ae-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.189.57",
                "ports": [
                    {
                        "name": "metrics",
                        "port": 9100,
                        "protocol": "TCP",
                        "targetPort": 9100
                    }
                ],
                "selector": {
                    "app": "prometheus-node-exporter",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app": "prometheus-operator-alertmanager",
                    "chart": "prometheus-operator-6.18.0",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "name": "prometheus-prometheus-oper-alertmanager",
                "namespace": "prometheus",
                "resourceVersion": "1862",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-alertmanager",
                "uid": "f782b095-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.223.31",
                "ports": [
                    {
                        "name": "web",
                        "port": 9093,
                        "protocol": "TCP",
                        "targetPort": 9093
                    }
                ],
                "selector": {
                    "alertmanager": "prometheus-prometheus-oper-alertmanager",
                    "app": "alertmanager"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app": "prometheus-operator-operator",
                    "chart": "prometheus-operator-6.18.0",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "name": "prometheus-prometheus-oper-operator",
                "namespace": "prometheus",
                "resourceVersion": "1869",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-operator",
                "uid": "f784a6ea-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.234.247",
                "ports": [
                    {
                        "name": "http",
                        "port": 8080,
                        "protocol": "TCP",
                        "targetPort": "http"
                    },
                    {
                        "name": "https",
                        "port": 443,
                        "protocol": "TCP",
                        "targetPort": "https"
                    }
                ],
                "selector": {
                    "app": "prometheus-operator-operator",
                    "release": "prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        },
        {
            "apiVersion": "v1",
            "kind": "Service",
            "metadata": {
                "creationTimestamp": "2019-12-23T08:48:18Z",
                "labels": {
                    "app": "prometheus-operator-prometheus",
                    "chart": "prometheus-operator-6.18.0",
                    "heritage": "Tiller",
                    "release": "prometheus"
                },
                "name": "prometheus-prometheus-oper-prometheus",
                "namespace": "prometheus",
                "resourceVersion": "1850",
                "selfLink": "/api/v1/namespaces/prometheus/services/prometheus-prometheus-oper-prometheus",
                "uid": "f77e1ac6-2560-11ea-83e0-0a20636a20d3"
            },
            "spec": {
                "clusterIP": "10.100.1.93",
                "ports": [
                    {
                        "name": "web",
                        "port": 9090,
                        "protocol": "TCP",
                        "targetPort": 9090
                    }
                ],
                "selector": {
                    "app": "prometheus",
                    "prometheus": "prometheus-prometheus-oper-prometheus"
                },
                "sessionAffinity": "None",
                "type": "ClusterIP"
            },
            "status": {
                "loadBalancer": {}
            }
        }
    ],
    "kind": "List",
    "metadata": {
        "resourceVersion": "",
        "selfLink": ""
    }
}
```

```console
Function [display_pods]: prometheus
NAME                                                     READY   STATUS    RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
prometheus-grafana-5c97446694-9bhc7                      2/2     Running   0          2m35s   192.168.37.136   ip-192-168-52-90.ec2.internal    <none>           <none>
prometheus-kube-state-metrics-5ffdf76ddd-f8pgx           1/1     Running   0          2m35s   192.168.38.138   ip-192-168-52-90.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-9nbsp                1/1     Running   0          2m35s   192.168.52.90    ip-192-168-52-90.ec2.internal    <none>           <none>
alertmanager-prometheus-prometheus-oper-alertmanager-0   2/2     Running   0          2m29s   192.168.71.52    ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-node-exporter-cnxtz                1/1     Running   0          2m35s   192.168.66.209   ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-oper-operator-6d59dcfb57-2crvb     2/2     Running   0          2m35s   192.168.89.83    ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-prometheus-oper-prometheus-0       3/3     Running   1          2m19s   192.168.64.76    ip-192-168-66-209.ec2.internal   <none>           <none>
```

```console
Function [deploy_dashboard]:
Creating Kubernetes Dashboard ...

secret/kubernetes-dashboard-certs created
serviceaccount/kubernetes-dashboard created
role.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
rolebinding.rbac.authorization.k8s.io/kubernetes-dashboard-minimal created
deployment.apps/kubernetes-dashboard created
service/kubernetes-dashboard created

Generating console-user and credentials ...

serviceaccount/admin-user created
clusterrolebinding.rbac.authorization.k8s.io/admin-user created

Displaying console-user configuration ...

Name:         admin-user-token-xn5nz
Namespace:    kube-system
Labels:       <none>
Annotations:  kubernetes.io/service-account.name: admin-user
              kubernetes.io/service-account.uid: 556e810c-2561-11ea-a71a-02287af92a37

Type:  kubernetes.io/service-account-token

Data
====
ca.crt:     1025 bytes
namespace:  11 bytes
token:      eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLXhuNW56Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI1NTZlODEwYy0yNTYxLTExZWEtYTcxYS0wMjI4N2FmOTJhMzciLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06YWRtaW4tdXNlciJ9.hPd7hlaTloIxTDGceoTYCKhvgke1mw7bNxVmuUey-kCX45-tSUlYjnHiXsbO7JY9hnRJBz5uMZBTxOgqy7WqJB4zkFygscywn1KvTHa7JzYEfSVDd7ND7UrKp79vFpjz8M4eMPsKEiNkbvBwPqSAVOmAoEmMpPC3PlSa17t1rf9W09CrmoT86va8vtnBac47dz9vQsUNUlrBH_Jc5gFt6eiUqkJKZzhMWhTqIIOXbCu9nreRIjrZOIHr1GL_gpRGstRzMBVwkmj4kzYJI0vfZPjhYuXqGru4GonleatOK5PBEB16gWKS5BEr-IOncfuKea1yew7qhJ97c8qAqoa7GQ

Execute: kubectl proxy ;
http://127.0.0.1:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/login

Console User-Token:

eyJhbGciOiJSUzI1NiIsImtpZCI6IiJ9.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJhZG1pbi11c2VyLXRva2VuLXhuNW56Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImFkbWluLXVzZXIiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiI1NTZlODEwYy0yNTYxLTExZWEtYTcxYS0wMjI4N2FmOTJhMzciLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06YWRtaW4tdXNlciJ9.hPd7hlaTloIxTDGceoTYCKhvgke1mw7bNxVmuUey-kCX45-tSUlYjnHiXsbO7JY9hnRJBz5uMZBTxOgqy7WqJB4zkFygscywn1KvTHa7JzYEfSVDd7ND7UrKp79vFpjz8M4eMPsKEiNkbvBwPqSAVOmAoEmMpPC3PlSa17t1rf9W09CrmoT86va8vtnBac47dz9vQsUNUlrBH_Jc5gFt6eiUqkJKZzhMWhTqIIOXbCu9nreRIjrZOIHr1GL_gpRGstRzMBVwkmj4kzYJI0vfZPjhYuXqGru4GonleatOK5PBEB16gWKS5BEr-IOncfuKea1yew7qhJ97c8qAqoa7GQ
```

```console
Deploy Prototype-Application (Y/n) ?: y

Function [cluster_application]:
Generating Application Container (Pod) ...

deployment.apps/helloworld-deployment created

Exposing Deployment Object (Load-Balancer) ...

service/helloworld-deployment exposed

Identifying Deployment Status ...

Waiting for deployment "helloworld-deployment" rollout to finish: 0 of 3 updated replicas are available...
Waiting for deployment "helloworld-deployment" rollout to finish: 1 of 3 updated replicas are available...
Waiting for deployment "helloworld-deployment" rollout to finish: 2 of 3 updated replicas are available...
deployment "helloworld-deployment" successfully rolled out
```

```console
Function [cluster_services]:
Listing Kubernetes Services:

NAME                    TYPE           CLUSTER-IP      EXTERNAL-IP                                                               PORT(S)          AGE
helloworld-deployment   LoadBalancer   10.100.162.98   a5740d528256111eaa71a02287af92a3-1480566631.us-east-1.elb.amazonaws.com   3000:30583/TCP   19s
kubernetes              ClusterIP      10.100.0.1      <none>                                                                    443/TCP          12m

Describing Application Service ...

Name:                     helloworld-deployment
Namespace:                default
Labels:                   <none>
Annotations:              <none>
Selector:                 app=helloworld
Type:                     LoadBalancer
IP:                       10.100.162.98
LoadBalancer Ingress:     a5740d528256111eaa71a02287af92a3-1480566631.us-east-1.elb.amazonaws.com
Port:                     <unset>  3000/TCP
TargetPort:               3000/TCP
NodePort:                 <unset>  30583/TCP
Endpoints:                192.168.33.101:3000,192.168.60.116:3000,192.168.87.199:3000
Session Affinity:         None
External Traffic Policy:  Cluster
Events:
  Type    Reason                Age   From                Message
  ----    ------                ----  ----                -------
  Normal  EnsuringLoadBalancer  20s   service-controller  Ensuring load balancer
  Normal  EnsuredLoadBalancer   18s   service-controller  Ensured load balancer


Name:              kubernetes
Namespace:         default
Labels:            component=apiserver
                   provider=kubernetes
Annotations:       <none>
Selector:          <none>
Type:              ClusterIP
IP:                10.100.0.1
Port:              https  443/TCP
TargetPort:        443/TCP
Endpoints:         192.168.113.174:443,192.168.178.220:443
Session Affinity:  None
Events:            <none>
```

```console
Function [cluster_replicationsets]:
Listing Replication Sets:

NAME                               DESIRED   CURRENT   READY   AGE
helloworld-deployment-79789c9f5d   3         3         3       21s
```

```console
Function [cluster_deployments]: default
Listing Deployment Objects [default]:

NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
helloworld-deployment   3/3     3            3           22s
```

```console
Function [extract_deployment]: helloworld-deployment
Cluster Deployment: helloworld-deployment-79789c9f5d-bpn87
```

```console
Describing Deployment: helloworld-deployment-79789c9f5d-bpn87

Function [describe_podname]: helloworld-deployment-79789c9f5d-bpn87
Name:           helloworld-deployment-79789c9f5d-bpn87
Namespace:      default
Priority:       0
Node:           ip-192-168-52-90.ec2.internal/192.168.52.90
Start Time:     Mon, 23 Dec 2019 01:50:58 -0700
Labels:         app=helloworld
                pod-template-hash=79789c9f5d
Annotations:    kubernetes.io/psp: eks.privileged
Status:         Running
IP:             192.168.33.101
IPs:            <none>
Controlled By:  ReplicaSet/helloworld-deployment-79789c9f5d
Containers:
  k8s-demo:
    Container ID:   docker://832d709eefb1665e9108d587cdecb41d2a52205004298ecacaf50e78adf58b08
    Image:          wardviaene/k8s-demo
    Image ID:       docker-pullable://wardviaene/k8s-demo@sha256:2c050f462f5d0b3a6430e7869bcdfe6ac48a447a89da79a56d0ef61460c7ab9e
    Port:           3000/TCP
    Host Port:      0/TCP
    State:          Running
      Started:      Mon, 23 Dec 2019 01:51:14 -0700
    Ready:          True
    Restart Count:  0
    Environment:    <none>
    Mounts:
      /var/run/secrets/kubernetes.io/serviceaccount from default-token-g7zwr (ro)
Conditions:
  Type              Status
  Initialized       True
  Ready             True
  ContainersReady   True
  PodScheduled      True
Volumes:
  default-token-g7zwr:
    Type:        Secret (a volume populated by a Secret)
    SecretName:  default-token-g7zwr
    Optional:    false
QoS Class:       BestEffort
Node-Selectors:  <none>
Tolerations:     node.kubernetes.io/not-ready:NoExecute for 300s
                 node.kubernetes.io/unreachable:NoExecute for 300s
Events:
  Type    Reason     Age   From                                    Message
  ----    ------     ----  ----                                    -------
  Normal  Scheduled  23s   default-scheduler                       Successfully assigned default/helloworld-deployment-79789c9f5d-bpn87 to ip-192-168-52-90.ec2.internal
  Normal  Pulling    21s   kubelet, ip-192-168-52-90.ec2.internal  Pulling image "wardviaene/k8s-demo"
  Normal  Pulled     10s   kubelet, ip-192-168-52-90.ec2.internal  Successfully pulled image "wardviaene/k8s-demo"
  Normal  Created    7s    kubelet, ip-192-168-52-90.ec2.internal  Created container k8s-demo
  Normal  Started    7s    kubelet, ip-192-168-52-90.ec2.internal  Started container k8s-demo
```

```console
Displaying Deployment's Log: helloworld-deployment-79789c9f5d-bpn87

npm info it worked if it ends with ok
npm info using npm@2.15.11
npm info using node@v4.6.2
npm info prestart myapp@0.0.1
npm info start myapp@0.0.1

> myapp@0.0.1 start /app
> node index.js

Example app listening at http://:::3000
```

```console
Describe Kubernetes Cluster (Y/n) ?: y
```

```console
Function [cluster_configuration]:

Listing Infrastructure Clusters ...

NAME
prototype.us-east-1.eksctl.io

Listing Kubernetes Configuration ...

apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: DATA+OMITTED
    server: https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com
  name: prototype.us-east-1.eksctl.io
contexts:
- context:
    cluster: prototype.us-east-1.eksctl.io
    user: kubernetes@prototype.us-east-1.eksctl.io
  name: kubernetes@prototype.us-east-1.eksctl.io
current-context: kubernetes@prototype.us-east-1.eksctl.io
kind: Config
preferences: {}
users:
- name: kubernetes@prototype.us-east-1.eksctl.io
  user:
    exec:
      apiVersion: client.authentication.k8s.io/v1alpha1
      args:
      - token
      - -i
      - prototype
      command: aws-iam-authenticator
      env:
      - name: AWS_PROFILE
        value: kubernetes
```

```console
Function [cluster_validation]:

Validating Kubernetes Cluster:  ...

Using cluster from kubectl context: prototype.us-east-1.eksctl.io


State Store: Required value: Please set the --state flag or export KOPS_STATE_STORE.
For example, a valid value follows the format s3://<bucket>.
You can find the supported stores in https://github.com/kubernetes/kops/blob/master/docs/state.md.
```

```console
Function [cluster_deployments]: kube-system
Listing Deployment Objects [kube-system]:

NAME                   READY   UP-TO-DATE   AVAILABLE   AGE
cluster-autoscaler     1/1     1            1           6m46s
cni-metrics-helper     1/1     1            1           5m39s
coredns                2/2     2            2           12m
kubernetes-dashboard   1/1     1            1           42s
metrics-server         1/1     1            1           6m51s
tiller-deploy          1/1     1            1           5m2s
```

```console
Function [display_apiservice]:

NAME                                   SERVICE                      AVAILABLE   AGE
v1.                                    Local                        True        12m
v1.apps                                Local                        True        12m
v1.authentication.k8s.io               Local                        True        12m
v1.authorization.k8s.io                Local                        True        12m
v1.autoscaling                         Local                        True        12m
v1.batch                               Local                        True        12m
v1.coordination.k8s.io                 Local                        True        12m
v1.monitoring.coreos.com               Local                        True        3m58s
v1.networking.k8s.io                   Local                        True        12m
v1.rbac.authorization.k8s.io           Local                        True        12m
v1.scheduling.k8s.io                   Local                        True        12m
v1.storage.k8s.io                      Local                        True        12m
v1alpha1.crd.k8s.amazonaws.com         Local                        True        9m32s
v1beta1.admissionregistration.k8s.io   Local                        True        12m
v1beta1.apiextensions.k8s.io           Local                        True        12m
v1beta1.apps                           Local                        True        12m
v1beta1.authentication.k8s.io          Local                        True        12m
v1beta1.authorization.k8s.io           Local                        True        12m
v1beta1.batch                          Local                        True        12m
v1beta1.certificates.k8s.io            Local                        True        12m
v1beta1.coordination.k8s.io            Local                        True        12m
v1beta1.events.k8s.io                  Local                        True        12m
v1beta1.extensions                     Local                        True        12m
v1beta1.metrics.k8s.io                 kube-system/metrics-server   True        6m52s
v1beta1.networking.k8s.io              Local                        True        12m
v1beta1.node.k8s.io                    Local                        True        12m
v1beta1.policy                         Local                        True        12m
v1beta1.rbac.authorization.k8s.io      Local                        True        12m
v1beta1.scheduling.k8s.io              Local                        True        12m
v1beta1.storage.k8s.io                 Local                        True        12m
v1beta2.apps                           Local                        True        12m
v2beta1.autoscaling                    Local                        True        12m
v2beta2.autoscaling                    Local                        True        12m
```

```console
Function [display_namespaces]:

NAME                                    CREATED AT
alertmanagers.monitoring.coreos.com     2019-12-23T08:47:40Z
eniconfigs.crd.k8s.amazonaws.com        2019-12-23T08:39:15Z
podmonitors.monitoring.coreos.com       2019-12-23T08:47:41Z
prometheuses.monitoring.coreos.com      2019-12-23T08:47:42Z
prometheusrules.monitoring.coreos.com   2019-12-23T08:47:43Z
servicemonitors.monitoring.coreos.com   2019-12-23T08:47:44Z
```

```console
Function [display_nodes]:

NAME                             STATUS   ROLES    AGE     VERSION              INTERNAL-IP      EXTERNAL-IP    OS-IMAGE         KERNEL-VERSION                  CONTAINER-RUNTIME
ip-192-168-52-90.ec2.internal    Ready    <none>   8m36s   v1.14.7-eks-1861c5   192.168.52.90    3.82.219.54    Amazon Linux 2   4.14.146-119.123.amzn2.x86_64   docker://18.6.1
ip-192-168-66-209.ec2.internal   Ready    <none>   8m51s   v1.14.7-eks-1861c5   192.168.66.209   3.87.238.174   Amazon Linux 2   4.14.146-119.123.amzn2.x86_64   docker://18.6.1
```

```console
Function [display_labels]:

Listing Kubernetes Nodes:

NAME                             STATUS   ROLES    AGE     VERSION              LABELS
ip-192-168-52-90.ec2.internal    Ready    <none>   8m37s   v1.14.7-eks-1861c5   alpha.eksctl.io/cluster-name=prototype,alpha.eksctl.io/nodegroup-name=devops,beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=m5.large,beta.kubernetes.io/os=linux,eks.amazonaws.com/nodegroup-image=ami-0392bafc801b7520f,eks.amazonaws.com/nodegroup=devops,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1b,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-192-168-52-90.ec2.internal,kubernetes.io/os=linux
ip-192-168-66-209.ec2.internal   Ready    <none>   8m52s   v1.14.7-eks-1861c5   alpha.eksctl.io/cluster-name=prototype,alpha.eksctl.io/nodegroup-name=devops,beta.kubernetes.io/arch=amd64,beta.kubernetes.io/instance-type=m5.large,beta.kubernetes.io/os=linux,eks.amazonaws.com/nodegroup-image=ami-0392bafc801b7520f,eks.amazonaws.com/nodegroup=devops,failure-domain.beta.kubernetes.io/region=us-east-1,failure-domain.beta.kubernetes.io/zone=us-east-1c,kubernetes.io/arch=amd64,kubernetes.io/hostname=ip-192-168-66-209.ec2.internal,kubernetes.io/os=linux
```

```console
Function [display_pods]: default
NAME                                     READY   STATUS    RESTARTS   AGE   IP               NODE                             NOMINATED NODE   READINESS GATES
helloworld-deployment-79789c9f5d-bpn87   1/1     Running   0          41s   192.168.33.101   ip-192-168-52-90.ec2.internal    <none>           <none>
helloworld-deployment-79789c9f5d-t88mw   1/1     Running   0          41s   192.168.60.116   ip-192-168-52-90.ec2.internal    <none>           <none>
helloworld-deployment-79789c9f5d-k4lmd   1/1     Running   0          41s   192.168.87.199   ip-192-168-66-209.ec2.internal   <none>           <none>
```

```console
Function [display_pods]: kube-system
NAME                                    READY   STATUS    RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
aws-node-t9nlt                          1/1     Running   0          8m38s   192.168.52.90    ip-192-168-52-90.ec2.internal    <none>           <none>
kubernetes-dashboard-5f7b999d65-jjvds   1/1     Running   0          45s     192.168.53.171   ip-192-168-52-90.ec2.internal    <none>           <none>
cni-metrics-helper-7b845dfdd4-vvw9k     1/1     Running   0          5m42s   192.168.52.3     ip-192-168-52-90.ec2.internal    <none>           <none>
coredns-56678dcf76-shwk5                1/1     Running   0          12m     192.168.39.216   ip-192-168-52-90.ec2.internal    <none>           <none>
kube-proxy-glnt4                        1/1     Running   0          8m38s   192.168.52.90    ip-192-168-52-90.ec2.internal    <none>           <none>
metrics-server-7fcf9cc98b-5fk9s         1/1     Running   0          6m54s   192.168.41.92    ip-192-168-52-90.ec2.internal    <none>           <none>
aws-node-nv7hm                          1/1     Running   0          8m53s   192.168.66.209   ip-192-168-66-209.ec2.internal   <none>           <none>
coredns-56678dcf76-5wk8r                1/1     Running   0          12m     192.168.65.72    ip-192-168-66-209.ec2.internal   <none>           <none>
kube-proxy-7bzxn                        1/1     Running   0          8m53s   192.168.66.209   ip-192-168-66-209.ec2.internal   <none>           <none>
cluster-autoscaler-85c6b59c96-wj7qj     1/1     Running   0          5m58s   192.168.86.113   ip-192-168-66-209.ec2.internal   <none>           <none>
tiller-deploy-54c98f988f-srz4r          1/1     Running   0          5m5s    192.168.82.224   ip-192-168-66-209.ec2.internal   <none>           <none>
```

```console
Function [display_pods]: prometheus
NAME                                                     READY   STATUS    RESTARTS   AGE     IP               NODE                             NOMINATED NODE   READINESS GATES
prometheus-grafana-5c97446694-9bhc7                      2/2     Running   0          3m22s   192.168.37.136   ip-192-168-52-90.ec2.internal    <none>           <none>
prometheus-kube-state-metrics-5ffdf76ddd-f8pgx           1/1     Running   0          3m22s   192.168.38.138   ip-192-168-52-90.ec2.internal    <none>           <none>
prometheus-prometheus-node-exporter-9nbsp                1/1     Running   0          3m22s   192.168.52.90    ip-192-168-52-90.ec2.internal    <none>           <none>
alertmanager-prometheus-prometheus-oper-alertmanager-0   2/2     Running   0          3m16s   192.168.71.52    ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-node-exporter-cnxtz                1/1     Running   0          3m22s   192.168.66.209   ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-oper-operator-6d59dcfb57-2crvb     2/2     Running   0          3m22s   192.168.89.83    ip-192-168-66-209.ec2.internal   <none>           <none>
prometheus-prometheus-prometheus-oper-prometheus-0       3/3     Running   1          3m6s    192.168.64.76    ip-192-168-66-209.ec2.internal   <none>           <none>
```

```console
Kubernetes master is running at https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com
CoreDNS is running at https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy
Metrics-server is running at https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com/api/v1/namespaces/kube-system/services/https:metrics-server:/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

```console
Function [display_ekscluster]:
[
    {
        "Arn": "arn:aws:eks:us-east-1:738054984624:cluster/prototype",
        "CertificateAuthority": {
            "Data": "LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSUN5RENDQWJDZ0F3SUJBZ0lCQURBTkJna3Foa2lHOXcwQkFRc0ZBREFWTVJNd0VRWURWUVFERXdwcmRXSmwKY201bGRHVnpNQjRYRFRFNU1USXlNekE0TXpneU9Wb1hEVEk1TVRJeU1EQTRNemd5T1Zvd0ZURVRNQkVHQTFVRQpBeE1LYTNWaVpYSnVaWFJsY3pDQ0FTSXdEUVlKS29aSWh2Y05BUUVCQlFBRGdnRVBBRENDQVFvQ2dnRUJBS21RCmJFRmZkTEdTSUU5YTgzY3ZIMFBqblJOZEo3aHN2VDV2UlpLcFlOZlg3TWdiZ0hVOG11WXdJYnZVQjJDSXZNK3kKN2M2QVozeUsrSTd5WjIxck5kSlBsaFV5RThZd09RdGJxOGNDdHl2RklFUnRxRXVrbmo2MW1ET01LTXFjeDdpQgpySTdHWVFrbmtYME83VUdhQWRpOExIaXBCTXdpTHI5bEhHQXhQSGx6V3pJcTdEUXNBc0VnaW9CTHhNVUtOaFRwCmljeFFIOVU2MXdtZGFIeXJ3WFRubm4vWGRBdUtmWVRmOWZzczlXa2ZDTTdCdmZzNjUxaUh5WVFsaDJJNjJCcTAKWWFDNUt1ODFkam4rZXVZak1TTFg1QlJrZTdDMFBqeHgzT0huek52R2lzVGNxcHNjZktuWVRRWStpT0IzNDh6SwpKYzRnYkNNWFl1djhUalB1bTVjQ0F3RUFBYU1qTUNFd0RnWURWUjBQQVFIL0JBUURBZ0trTUE4R0ExVWRFd0VCCi93UUZNQU1CQWY4d0RRWUpLb1pJaHZjTkFRRUxCUUFEZ2dFQkFIZ3RsSk9zTWkraWZST1RMWERrLzhwbksyOHIKNGdvWFpCTXNoaVpKYXhWMWo1WURTSUc5dzZlNUUyZlQ3d05Ud0ZLWWk2MXNodERIK1NLaGRRaFBtN1FaLy9EOAphaGRORnNpTkdYVHhMVzhPSlNXa1graWZXWStKS3AzWWVlWkN1bDFYd3lkc0xsMGJSYldaNVBEdk9VQW1jNng3CmcyZEMyekxBaklRdU1KbHdjWGFEYmF6UzRra1VSVkpWZFNpUW5tOW5nZmttWDZrSmtJeDJENmZjV0FSeUFZVGgKVGJsWFFoMGY5L2YweDdIUHNvOFBWeDJXV1JRbnZoanlnVVlOK3BUNEduTm9DZkliVHBVS2pOQjJsMkpjNElZawpUVmhKSHlSaVNzSWZLL1J5T0F0RWxvckRqU0N4YXFmV2tVU0pYZXFjM2IvVkJIa1RVeVhvRElwTEVYTT0KLS0tLS1FTkQgQ0VSVElGSUNBVEUtLS0tLQo="
        },
        "ClientRequestToken": null,
        "CreatedAt": "2019-12-23T08:29:20Z",
        "Endpoint": "https://31D0097B30C6300A1AD47CD740DB4E4E.yl4.us-east-1.eks.amazonaws.com",
        "Identity": {
            "Oidc": {
                "Issuer": "https://oidc.eks.us-east-1.amazonaws.com/id/31D0097B30C6300A1AD47CD740DB4E4E"
            }
        },
        "Logging": {
            "ClusterLogging": [
                {
                    "Enabled": true,
                    "Types": [
                        "api",
                        "audit",
                        "authenticator",
                        "controllerManager",
                        "scheduler"
                    ]
                }
            ]
        },
        "Name": "prototype",
        "PlatformVersion": "eks.6",
        "ResourcesVpcConfig": {
            "ClusterSecurityGroupId": "sg-0802d870efe4f66a2",
            "EndpointPrivateAccess": false,
            "EndpointPublicAccess": true,
            "SecurityGroupIds": [
                "sg-054594ae12482ff56"
            ],
            "SubnetIds": [
                "subnet-0f5f396fc169fa3cc",
                "subnet-09a7c44bb0d763ea1",
                "subnet-0f2ee3e2b65f9660f",
                "subnet-06f80d112a35bcbc5",
                "subnet-088cf0f3c3ca8d8a3",
                "subnet-03804f05568eb39ba"
            ],
            "VpcId": "vpc-094eb6f95cb478207"
        },
        "RoleArn": "arn:aws:iam::738054984624:role/eksctl-prototype-cluster-ServiceRole-1NTUNUAY288AO",
        "Status": "ACTIVE",
        "Tags": {},
        "Version": "1.14"
    }
]
```

```console
Completed!
```

```console
$ eksctl delete cluster --region=us-west-2 --name=prototype ;

[ℹ]  eksctl version 0.25.0
[ℹ]  using region us-west-2
[ℹ]  deleting EKS cluster "prototype"
[ℹ]  deleting Fargate profile "fp-default"
[ℹ]  deleted Fargate profile "fp-default"
[ℹ]  deleted 1 Fargate profile(s)
[ℹ]  cleaning up AWS load balancers created by Kubernetes objects of Kind Service or Ingress
[ℹ]  2 sequential tasks: { delete nodegroup "devops", delete cluster control plane "prototype" [async] }
[ℹ]  will delete stack "eksctl-prototype-nodegroup-devops"
[ℹ]  waiting for stack "eksctl-prototype-nodegroup-devops" to get deleted
[ℹ]  will delete stack "eksctl-prototype-cluster"
[✔]  all cluster resources were deleted
```

```console
Completed!
```
