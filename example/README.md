# Example usage from scratch
- Install terraform
- Modify the `terraform.tfvars` file:
```hcl
region = "dev" # or "us-east" or "eu-west"
uaa_username = "your_ldap_username"
uaa_password = "your_ldap_password"
serial_number = "YOUR_STL_DEVICE_SERIAL"
```

- Edit the `main.tf` file, it looks like this:

```hcl
module "app" {
  source = "philips-labs/stl-app/hsdp"
  version = "0.1.0"
  
  serial_number = var.serial_number
  app_name = "grafana"
  docker_image = "grafana/grafana:latest"
  container_port = 3000
}
```

- Run `terraform init`
- Run `terrform plan`
- Run `terraform apply`
