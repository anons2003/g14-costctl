# sample_output/

These files are real outputs generated from the W6 AWS account using
`AWS_PROFILE=w6self` and `AWS_REGION=us-east-1` on 2026-05-22.

## How to produce real samples

```bash
AWS_PROFILE=w6self ./costctl.py list ec2 > sample_output/list_ec2_2026-05-22.txt
AWS_PROFILE=w6self ./costctl.py list ec2 --missing-tag Application > sample_output/list_ec2_missing_app_2026-05-22.txt
AWS_PROFILE=w6self ./costctl.py cost --tag Name=aws-lab-ec2 --days 7 > sample_output/cost_aws-lab-ec2_2026-05-22.txt
```

The cost output is valid even though it is `$0.00`: the `Name=aws-lab-ec2`
tag is present on the EC2 instance, but Cost Explorer only returns tag-filtered
costs for activated cost allocation tags.
