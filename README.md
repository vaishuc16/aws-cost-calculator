# AWS Cloud Cost Calculator

A serverless project that tracks my AWS spending and shows it on a dashboard.

## How it works
- **Lambda (Python)** gets the last 7 days of cost from the Cost Explorer API
- **S3** stores the report as `data.json` and hosts the dashboard page
- **CloudWatch alarm + SNS** emails me when estimated charges cross a limit
- **IAM** gives Lambda only the permissions it needs
- **EventBridge** runs it weekly

## Files
- `lambda_function.py`: the Lambda code
- `index.html`: the dashboard page

## Problems I fixed
- Lambda AccessDenied: added a least-privilege IAM policy
- NoSuchBucket: corrected the bucket name in the environment variable
- S3 403 error: unblocked public access and added an IP-restricted bucket policy
- Dashboard showed $0: Free plan credits hide costs, so I filtered out credits

## Screenshots
See the `screenshots` folder.
