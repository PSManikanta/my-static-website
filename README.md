# my-static-website

This repository contains a static website and a GitHub Actions CI/CD pipeline to deploy it to Amazon S3.

## Website files
- `public/index.html` - main static webpage.

## CI/CD workflow
- Workflow file: `.github/workflows/deploy-to-s3.yml`
- Triggered on pushes to `main` and manual dispatch.
- Uses OpenID Connect (OIDC) via `aws-actions/configure-aws-credentials`.
- Syncs repository website content to the target S3 bucket.

## Required GitHub configuration
Set the following before running the workflow:

### Repository Secrets
- `AWS_ROLE_TO_ASSUME`: IAM role ARN that GitHub Actions can assume.

### Repository Variables
- `AWS_REGION`: AWS region where the bucket exists (for example `us-east-1`).
- `S3_BUCKET_NAME`: Name of the S3 bucket used for website hosting.

## Notes
- Ensure static website hosting is enabled on the S3 bucket.
- The IAM role should allow `s3:ListBucket`, `s3:GetObject`, `s3:PutObject`, and `s3:DeleteObject` for the target bucket.
