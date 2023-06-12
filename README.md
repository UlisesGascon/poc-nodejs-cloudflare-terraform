# Cloudflare Infrastructure

Repository to manage Node.js Cloudflare settings using Terraform

### Contributing

To modify the Cloudflare settings, you must fork/clone this repository and submit a pull request with the changes. Any alterations made in the `main` branch will be deployed to the Cloudflare account automatically.

### Historical Context

Today, we use Terraform to manage DNS records in Cloudflare. Previously, we used the Cloudflare UI for this task. To begin using Terraform, we cloned the Cloudflare settings and migrated them as the initial Terraform state using the utility cf-terraforming. This step was completed only once, and the state was stored in Terraform Cloud.

Since the imported resources had non-human friendly names like "terraform_managed_resource_*," we cannot change their names to prevent recreation or updates of the resources. However, we can use our own naming conventions for new Terraform resources, and there is no need to run the cf-terraforming utility again.


#### Side notes

- Terraform version `Terraform v1.4.5 on darwin_amd64`
- Use [Cloudflare Terraforming](https://github.com/cloudflare/cf-terraforming) to bring the cloudflare resources, like `cf-terraforming generate --resource-type "cloudflare_record" --zone {ZONE_ID} --token {TOKEN} > imported.tf` and then import them to the state `cf-terraforming import --resource-type "cloudflare_record" --zone {ZONE_ID} --token {TOKEN}`
- Use Terraform cloud to safely store the state 
- Add the token `TF_API_TOKEN` in the Github actions with a valid Terraform cloud API Key

#### Reference
- [Terraform Cheatsheet](https://acloudguru.com/blog/engineering/the-ultimate-terraform-cheatsheet)
- [Youtube | Automate Cloudflare with Terraform and GitHub Actions! - Terraform Tutorial for Beginners](https://www.youtube.com/watch?v=FmYvrxYvBP0)
- [Techno Tim Docs | Automate Cloudflare with Terraform and GitHub Actions! - Terraform Tutorial for Beginners](https://docs.technotim.live/posts/terraform-cloudflare-github/)