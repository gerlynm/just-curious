# CloudFront OAI vs OAC Terraform Demo

This repository helps you quickly test and compare AWS CloudFront’s **Origin Access Identity (OAI)** and **Origin Access Control (OAC)** methods for accessing private S3 buckets.

---

## Getting Started

### 1. Test **OAI** (Legacy Approach)

1. Clone this repo:

   ```bash
   git clone https://github.com/gerlynm/just-curious.git
   cd cloudfront/oai-oac

   ```

2. Initialize Terraform:

   ```bash
   terraform init
   ```

3. Apply Terraform configuration (this will create **one S3 bucket** and **two CloudFront distributions** using the same OAI):

   ```bash
   terraform apply
   ```

4. Confirm resources are created and test access as needed.

---

### 2. Test **OAC** (Modern Approach)

1. After testing OAI, open the `terraform.tfvars` file in the same folder.

2. Change the variable `enable_oac` to `true`:

   ```hcl
   enable_oac = true
   ```

3. Re-apply Terraform to update the infrastructure and switch to OAC setup (this will create **two new CloudFront distributions** with OAC and update the S3 bucket policy accordingly):

   ```bash
   terraform apply
   ```

4. Verify that only CloudFront distributions with OAC can access the S3 bucket.

---

## Notes

- When `enable_oac` is `true`, only OAC-related resources and policies are created. OAI resources are not created or removed but existing s3 bucket policy will be altered.
- Switching back to `false` will revert to the OAI setup.
- This setup helps you see firsthand how the two approaches differ in access control and security.

---

## Cleanup

When finished, run:

```bash
terraform destroy
```

to remove all created AWS resources and avoid ongoing charges.

---

## Questions?

Feel free to open an issue or contact me if you need any help running the demo!

---

**Happy experimenting!** 🚀
