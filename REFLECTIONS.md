# Reflections

## Multi-account

To run `costctl` against 100 AWS accounts, I would add an account inventory file
and make the CLI assume a read-only or cost-ops role in each account. The output
should include the account id/name on every row and support CSV export so the
results can be aggregated, sorted, and reviewed before taking action.

## `clean --apply` blast radius

If `clean --tag Environment=dev --apply` was run in a shared account, I would
want multiple guardrails before deletion: a dry-run summary by default, an
explicit allowlist of account ids, required ownership tags, and a second
confirmation showing the exact resource ids. For production use, I would also
add IAM permissions that only allow destructive actions on resources tagged for
practice cleanup.

## AI assistance

AI helped draft most of the command bodies, but I actively checked the tests,
docstrings, boto3 API behavior, and real AWS login behavior. One manual change
was adding `botocore[crt]` because the `aws login` credential provider needs
the CRT dependency for boto3 to use the `w6self` profile.
