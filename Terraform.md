
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

