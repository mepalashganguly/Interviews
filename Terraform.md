
## Terraform

<a name="Cloud Migration"></a>

<details>
<summary>1.1 - what are Provider-defined functions?</summary><br><b>
  
Provider-defined functions in Terraform are a feature introduced in Terraform 1.8 that allows providers to expose custom functions specific to their domain or use case. These functions extend Terraform's built-in function capabilities by enabling providers (like AWS, Google Cloud, Kubernetes, etc.) to implement pure functions that perform offline computational tasks or data transformations relevant to their platform.

Example:
provider::provider_name::function_name(arguments)

provider::terraform::encode_tfvars({
  example = "Hello!"
})

</b></details>

<details>
<summary>1.2 - What Terraform refresh do?</summary><br><b>
The terraform refresh command does NOT make any changes to cloud/platform resources—it only updates the Terraform state file with the actual state of resources as found in your target infrastructure.

What does terraform refresh do?
Connects to your provider (like AWS, Azure, etc.).

Reads the real state of all resources defined in your configuration.

Updates the local state file (terraform.tfstate) to match what’s actually present in your cloud account.

Useful for making Terraform aware of changes made outside of Terraform (“drift detection”).

What does it NOT do?
It does not create, update, or destroy any resources in your cloud platform.

It is a read-only operation with respect to your infrastructure.

When would the platform actually change?
When you run terraform apply (or terraform destroy), Terraform will attempt to modify resources to match your configuration and state.

terraform refresh only changes the state file locally, never the real cloud infrastructure.

Summary:

terraform refresh NEVER changes your actual platform/cloud resources—it just synchronizes your state file with reality.

It’s safe to run if you want to update your state after external changes, but use plan or apply when you want Terraform to affect real infrastructure.
</b></details>
