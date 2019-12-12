# serverless-cdn

[![serverless](http://public.serverless.com/badges/v3.svg)](http://www.serverless.com)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/smoketurner/serverless-cdn/master/LICENSE)

[Serverless](https://serverless.com) project that deploys a content delivery network (CDN) using AWS CloudFront for static assets hosted in a private S3 bucket.

This projects creates the following resources:

- `AWS::CertificateManager::Certificate` - `*.<domain>` SSL certificate
- `AWS::CloudFront::Distribution` - `[http|https]://<domain>` distribution
- `AWS::CloudFront::Distribution` - `[http|https]://www.<domain>` redirect distribution
- `AWS::CloudFront::CloudFrontOriginAccessIdentity`
- `AWS::Route53::RecordSet` - `<domain>` IPv4 DNS entry
- `AWS::Route53::RecordSet` - `<domain>` IPv6 DNS entry
- `AWS::Route53::RecordSet` - `www.<domain>` IPv4 DNS entry
- `AWS::Route53::RecordSet` - `www.<domain>` IPv6 DNS entry
- `AWS::S3::Bucket` - access log bucket
- `AWS::S3::Bucket` - static asset bucket
- `AWS::S3::Bucket` - bucket to redirect requests to `https://<domain>`
- `AWS::S3::BucketPolicy` - only allow CloudFront to access static asset bucket
- `AWS::Lambda::Function` - Lambda@Edge function for single page applications to redirect requests to `/index.html`
- `AWS::Lambda::Function` - Lambda@Edge function to add various web security HTTP response headers

## Installation

```
git clone https://github.com/smoketurner/serverless-cdn.git
cd serverless-cdn
npm install
```

## Run Tests

```
npm test
```

## Deploy

```
npm run deploy
```

## Removal

```
npm run remove
```

## References

- https://www.awsadvent.com/2018/12/03/vanquishing-cors-with-cloudfront-and-lambdaedge/
- https://medium.com/faun/hardening-the-http-security-headers-with-aws-lambda-edge-and-cloudfront-2e2da1ae4d83
