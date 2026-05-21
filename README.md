# DevOps Projects — Static Website on AWS S3

A hands-on DevOps mini-project that hosts a static HTML/CSS/JS website on **Amazon S3** with public access and S3 website hosting enabled.

## What this project does

Uploads a static site to an S3 bucket, configures the bucket for website hosting, and exposes it on a public S3 URL. A good starting point before adding CloudFront, HTTPS, and a custom domain.

## Prerequisites

An AWS account with permission to create and configure S3 buckets. AWS CLI configured.

## Steps

```bash
# 1. Create the bucket
aws s3 mb s3://my-devops-static-site

# 2. Upload the site
aws s3 sync . s3://my-devops-static-site --exclude "*.md" --acl public-read

# 3. Enable static website hosting
aws s3 website s3://my-devops-static-site --index-document index.html --error-document error.html
```

The site will be reachable at `http://my-devops-static-site.s3-website-<region>.amazonaws.com`.

## Next steps

Put CloudFront in front of S3 for HTTPS and global caching. Add Route 53 for a custom domain. Automate with Terraform or GitHub Actions.

## License

MIT
