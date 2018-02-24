# Run Hugo on AWS

## Setup S3

Here are the commands executed when following the instruction
from: https://lustforge.com/2016/02/27/hosting-hugo-on-aws/


Step 1)
```
# Set your domain here
YOUR_DOMAIN="pbx-group-security.com"
REGION="us-east-1"
# Don't change these
BUCKET_NAME="pbx-group-security.com-cdn"
LOG_BUCKET_NAME="pbx-group-security.com-logs"

# One fresh bucket please!
aws s3 mb s3://$BUCKET_NAME --region $REGION
# And another for the logs
aws s3 mb s3://$LOG_BUCKET_NAME --region $REGION
```

Step 2)

```
# Let AWS write the logs to this location
aws s3api put-bucket-acl --bucket $LOG_BUCKET_NAME \
                         --grant-write 'URI="http://acs.amazonaws.com/groups/s3/LogDelivery"' \
                         --grant-read-acp 'URI="http://acs.amazonaws.com/groups/s3/LogDelivery"'

# Setup logging
LOG_POLICY="{\"LoggingEnabled\":{\"TargetBucket\":\"$LOG_BUCKET_NAME\",\"TargetPrefix\":\"$BUCKET_NAME\"}}"
aws s3api put-bucket-logging --bucket $BUCKET_NAME --bucket-logging-status $LOG_POLICY

Step 3)

# Create website config
echo "{
    \"IndexDocument\": {
        \"Suffix\": \"index.html\"
    },
    \"ErrorDocument\": {
        \"Key\": \"404.html\"
    },
    \"RoutingRules\": [
        {
            \"Redirect\": {
                \"ReplaceKeyWith\": \"index.html\"
            },
            \"Condition\": {
                \"KeyPrefixEquals\": \"/\"
            }
        }
    ]
}" > website.json

aws s3api put-bucket-website --bucket $BUCKET_NAME --website-configuration file://website.json
```


Step 4)


open http://pbx-group-security.com-cdn.s3-website.$REGION.amazonaws.com/

Step 5)

aws acm request-certificate --domain-name $YOUR_DOMAIN --subject-alternative-names "www.$YOUR_DOMAIN" --idempotency-token "`date +%s`"


Step 6)

aws acm list-certificates --certificate-statuses ISSUED

# Example result
{
    "CertificateSummaryList": [
        {
            "CertificateArn": "arn:aws:acm:us-east-1:244560807427:certificate/0601849b-230a-45e8-bb71-b6e085605483",
            "DomainName": "pbx-group-security.com"
        }
    ]
}

Step 7)

aws  configure  set preview.cloudfront true

Step 8)

```
# From above
SSL_ARN="arn:aws:acm:us-east-1:244560807427:certificate/0601849b-230a-45e8-bb71-b6e085605483"

CALLER_REF="`date +%s`" # current second
echo "{
    \"Comment\": \"$BUCKET_NAME Static Hosting\",
    \"Logging\": {
        \"Bucket\": \"$LOG_BUCKET_NAME.s3.amazonaws.com\",
        \"Prefix\": \"${BUCKET_NAME}-cf/\",
        \"Enabled\": true,
        \"IncludeCookies\": false
    },
    \"Origins\": {
        \"Quantity\": 1,
        \"Items\": [
            {
                \"Id\":\"$BUCKET_NAME-origin\",
                \"OriginPath\": \"\",
                \"CustomOriginConfig\": {
                    \"OriginProtocolPolicy\": \"http-only\",
                    \"HTTPPort\": 80,
                    \"OriginSslProtocols\": {
                        \"Quantity\": 3,
                        \"Items\": [
                            \"TLSv1\",
                            \"TLSv1.1\",
                            \"TLSv1.2\"
                        ]
                    },
                    \"HTTPSPort\": 443
                },
                \"DomainName\": \"$BUCKET_NAME.s3-website-$REGION.amazonaws.com\"
            }
        ]
    },
    \"DefaultRootObject\": \"index.html\",
    \"PriceClass\": \"PriceClass_All\",
    \"Enabled\": true,
    \"CallerReference\": \"$CALLER_REF\",
    \"DefaultCacheBehavior\": {
        \"TargetOriginId\": \"$BUCKET_NAME-origin\",
        \"ViewerProtocolPolicy\": \"redirect-to-https\",
        \"DefaultTTL\": 1800,
        \"AllowedMethods\": {
            \"Quantity\": 2,
            \"Items\": [
                \"HEAD\",
                \"GET\"
            ],
            \"CachedMethods\": {
                \"Quantity\": 2,
                \"Items\": [
                    \"HEAD\",
                    \"GET\"
                ]
            }
        },
        \"MinTTL\": 0,
        \"Compress\": true,
        \"ForwardedValues\": {
            \"Headers\": {
                \"Quantity\": 0
            },
            \"Cookies\": {
                \"Forward\": \"none\"
            },
            \"QueryString\": false
        },
        \"TrustedSigners\": {
            \"Enabled\": false,
            \"Quantity\": 0
        }
    },
    \"ViewerCertificate\": {
        \"SSLSupportMethod\": \"sni-only\",
        \"ACMCertificateArn\": \"$SSL_ARN\",
        \"MinimumProtocolVersion\": \"TLSv1\",
        \"Certificate\": \"$SSL_ARN\",
        \"CertificateSource\": \"acm\"
    },
    \"CustomErrorResponses\": {
        \"Quantity\": 2,
        \"Items\": [
            {
                \"ErrorCode\": 403,
                \"ResponsePagePath\": \"/404.html\",
                \"ResponseCode\": \"404\",
                \"ErrorCachingMinTTL\": 300
            },
            {
                \"ErrorCode\": 404,
                \"ResponsePagePath\": \"/404.html\",
                \"ResponseCode\": \"404\",
                \"ErrorCachingMinTTL\": 300
            }
        ]
    },
    \"Aliases\": {
        \"Quantity\": 2,
        \"Items\": [
            \"$YOUR_DOMAIN\",
            \"www.$YOUR_DOMAIN\"
        ]
    }
}" > distroConfig.json

```
Step 9)

Check email and validate request

https://console.aws.amazon.com/acm/home?region=us-east-1#/

Step 10)
```
# Now apply it
    aws cloudfront create-distribution --distribution-config file://distroConfig.json
```

Step 11)

```
aws cloudfront list-distributions --query 'DistributionList.Items[].{id:Id,comment:Comment,domain:DomainName}'

[
    {
        "comment": "pbx-group-security.com-cdn Static Hosting",
        "domain": "d2w4wfd51ihke0.cloudfront.net",
        "id": "E3K53GHHL4D0LE"
    }
]
```

Step 12)

```
aws route53 list-hosted-zones

        {
            "ResourceRecordSetCount": 2,
            "CallerReference": "RISWorkflow-RD:45708f96-e328-4779-b798-4a0c0395b29c",
            "Config": {
                "Comment": "HostedZone created by Route53 Registrar",
                "PrivateZone": false
            },
            "Id": "/hostedzone/Z1ARCEL6PLWFV6",
            "Name": "pbx-group-security.com."
        }
```


Step 13)
```
HOSTED_ZONE_ID="/hostedzone/Z1ARCEL6PLWFV6"
DISTRO_URL="d2w4wfd51ihke0.cloudfront.net"

echo "{
    \"Comment\": \"Let there be Hugo!\",
    \"Changes\": [
        {
            \"Action\":\"UPSERT\",
            \"ResourceRecordSet\": {
                \"AliasTarget\": {
                    \"HostedZoneId\": \"Z2FDTNDATAQYW2\",
                    \"EvaluateTargetHealth\": false,
                    \"DNSName\": \"$DISTRO_URL.\"
                },
                \"Type\": \"A\",
                \"Name\": \"$YOUR_DOMAIN.\"
            }
        },{
            \"Action\":\"UPSERT\",
            \"ResourceRecordSet\": {
                \"ResourceRecords\": [
                    {
                        \"Value\": \"$DISTRO_URL\"
                    }
                ],
                \"Type\": \"CNAME\",
                \"Name\": \"www.$YOUR_DOMAIN.\",
                \"TTL\": 300
            }
        }
    ]
}" > r53Batch.json

aws route53 change-resource-record-sets --hosted-zone-id $HOSTED_ZONE_ID --change-batch file://r53Batch.json
```

```
{
    "ChangeInfo": {
        "Status": "PENDING",
        "SubmittedAt": "2017-12-02T18:43:46.270Z",
        "Id": "/change/C2DXGXR6EB1DJX"
    }
}
```

## Deploying files

Now following https://lustforge.com/2016/02/28/deploy-hugo-files-to-s3/

Step 1)

```
set -e # Fail fast

DISTRIBUTION_ID=E3K53GHHL4D0LE
BUCKET_NAME=pbx-group-security.com-cdn

# Build a fresh copy
hugo -v

# Copy over pages - not static js/img/css/downloads
aws s3 sync --acl "public-read" --sse "AES256" public/ s3://$BUCKET_NAME --exclude 'post'

# Invalidate root page and page listings
aws cloudfront create-invalidation --distribution-id $DISTRIBUTION_ID --paths /index.html / /page/*

```

Step 2)