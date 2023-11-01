# Updating the Landing Zone Accelerator version

To upgrade your LZA to the latest version you should follow the [update instructions from the LZA implementation guide](https://docs.aws.amazon.com/solutions/latest/landing-zone-accelerator-on-aws/update-the-solution.html). The current page contains additional instructions specific to this reference configuration.

### Update Preparation

Before proceeding with the update you should carefully review the release notes for every version and identify any configuration changes that are mandatory or recommended.

- Review the [LZA release notes](https://github.com/awslabs/landing-zone-accelerator-on-aws/releases)
- Review new configuration items from the LZA release notes, assess the new defaults and integrate them into your configuration
- Review configuration changes to the [default configuration files](./config/) and determine which change you need to apply to your configuration
- Review this configuration [CHANGELOG](CHANGELOG.md)

### General update steps

1. Login to your Organization Management (root) AWS account with administrative privileges
2. Either: a) Ensure a valid Github token is stored in secrets manager ([per the installation guide](https://docs.aws.amazon.com/solutions/latest/landing-zone-accelerator-on-aws/prerequisites.html#create-a-github-personal-access-token-and-store-in-secrets-manager)), or b) Ensure the latest release is in a valid branch of CodeCommit in the Organization Management account
3. Before updating: Run the pipeline with the current version and confirm a sucessful execution
4. Review and implement any relevant tasks noted in the **Update Preparation** section above
5. Update the configuration files in the `aws-accelerator-config` **CodeCommit** repository as outlined in the **Update Preparation** section above
6. Sign in to the AWS CloudFormation console, select your existing Landing Zone Accelerator on AWS CloudFormation stack and Update the stack with the latest template available from the release page. ([refer to the LZA implementation guide for detailed steps](https://docs.aws.amazon.com/solutions/latest/landing-zone-accelerator-on-aws/update-the-solution.html))
7. When reviewing the Stack Parameters, make sure to update the `RepositoryBranchName` value to point to the branch of the latest release (i.e. release/v.X.Y.Z)
8. Wait for successful execution of the Landing Zone Accelerator stack update and the `AWSAccelerator-Installer` and `AWSAccelerator-Pipeline` pipelines

