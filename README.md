# Psoxy Deployment Example - GCP

![build passing](https://img.shields.io/github/actions/workflow/status/Worklytics/psoxy-example-gcp/terraform_validate.yaml?label=build%20passing)

This is a template repo for a Terraform configuration that deploys the [Worklytics pseudonymization
proxy (psoxy)](https://github.com/Worklytics/psoxy) on GCP.

## Usage

### Prereqs

You'll need:
- a Bash-like shell environment on Linux, MacOS, or [WSL on Windows](https://learn.microsoft.com/en-us/windows/wsl/install).
- [`git` installed](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git), although it
  is usually included on those platforms (check with `git --version`).
- an GCP project account and credentials, as described in [Psoxy's Getting Started - GCP docs](https://github.com/Worklytics/psoxy/blob/v0.4.17/docs/gcp/getting-started.md)
- the [prerequisites for Psoxy](https://github.com/Worklytics/psoxy/blob/v0.4.17/README.md#prerequisites)
  itself, although this example will attempt to help you check those

### Setup

See [GitHub's documentation](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template)
for more details.

1. Click the 'Use this template' button in the upper right corner of [this page](https://github.com/Worklytics/psoxy-example-gcp).
    - choose a name for your copy of this repo
    - leave "Include all branches" unchecked

2. Clone the resulting repo to your machine.  Example command below, just fill in your org and repo
   names.

```shell
git clone https://github.com/{{YOUR_ORG_ID}}/{{YOUR_REPO_NAME}}.git
```

3. Check your prereqs. Review versions and install anything needed.

```shell
./check-prereqs
```

4. Authenticate your tools as needed:

- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html) - `aws get-caller-identity` should work and return your expected account/user
- if plan to get data from Google Workspace, auth [GCloud CLI](https://cloud.google.com/sdk/docs/authorizing) - `gcloud auth login` to authenticate, then `gcloud auth list` to verify you have expected account/user

5. Initialize your configuration

```shell
./init
```

6. Review your `terraform.tfvars` file; customize as needed (eg, comment out datasources you don't need).

7. Run `terraform plan` and review results to understand what will be created. Customize your
   `terraform.tfvars` or `main.tf` file if needed.

```shell
terraform plan
```

8. Run `terraform apply` to create the resources.
```shell
terraform apply
```
