Terraform Module for creating Data Transmission Service (DTS) on Alibaba Cloud.

terraform-alicloud-dts
=====================================================================

English | [简体中文](README-CN.md)

This Module is used to automatically build and data transmission services based on DTS, including data synchronization instances, data synchronization jobs, and monitoring rules.

These types of resources are supported:

* [alicloud_dts_synchronization_instance](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/dts_synchronization_instance)
* [alicloud_dts_synchronization_job](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/dts_synchronization_job)
* [alicloud_dts_job_monitor_rule](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs/resources/dts_job_monitor_rule)

## Usage

<div style="display: block;margin-bottom: 40px;"><div class="oics-button" style="float: right;position: absolute;margin-bottom: 10px;">
  <a href="https://api.aliyun.com/terraform?source=Module&activeTab=document&sourcePath=terraform-alicloud-modules%3A%3Adts&spm=docs.m.terraform-alicloud-modules.dts&intl_lang=EN_US" target="_blank">
    <img alt="Open in AliCloud" src="https://img.alicdn.com/imgextra/i1/O1CN01hjjqXv1uYUlY56FyX_!!6000000006049-55-tps-254-36.svg" style="max-height: 44px; max-width: 100%;">
  </a>
</div></div>

```hcl
module "default" {
  source = "terraform-alicloud-modules/dts/alicloud"

  create_sync_instance               = "true"
  auto_pay                           = "true"
  auto_start                         = "true"
  payment_type                       = "PayAsYouGo"
  source_endpoint_region             = "cn-hangzhou"
  destination_endpoint_region        = "cn-hangzhou"
  instance_class                     = "small"
  create_sync_job                    = true
  synchronization_bidirectional      = true
  dts_job_name                       = "tf-testAccCase"
  data_initialization                = "true"
  data_synchronization               = "true"
  structure_initialization           = "true"
  source_endpoint_instance_id        = "rm-bp1gxxxxxxxxjv"
  source_endpoint_database_name      = "source_database"
  source_endpoint_user_name          = "username"
  source_endpoint_password           = "password"
  destination_endpoint_instance_id   = "rm-bp1gxxxxxxxxka"
  destination_endpoint_database_name = "destination_database"
  destination_endpoint_user_name     = "username"
  destination_endpoint_password      = "password"
  db_list                            = "{\"test_database\":{\"name\":\"test_database\",\"all\":true,\"state\":\"normal\"}}"
  dts_job_status                     = "Synchronizing"
  create_monitor_rule                = false
}
```

## Examples

* [DTS complete example](https://github.com/terraform-alicloud-modules/terraform-alicloud-dts/tree/main/examples/complete)

## Notes

* This module using AccessKey and SecretKey are from `profile` and `shared_credentials_file`. If you have not set them
  yet, please install [aliyun-cli](https://github.com/aliyun/aliyun-cli#installation) and configure it.

## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | > = 0.13 |
| <a name="requirement_alicloud"></a> [alicloud](#requirement\_alicloud) | > = 1.138.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_alicloud"></a> [alicloud](#provider\_alicloud) | > = 1.138.0 |

## Submit Issues

If you have any problems when using this module, please opening
a [provider issue](https://github.com/aliyun/terraform-provider-alicloud/issues/new) and let us know.

**Note:** There does not recommend opening an issue on this repo.

## Authors

Created and maintained by Alibaba Cloud Terraform Team(terraform@alibabacloud.com).

## License

MIT Licensed. See LICENSE for full details.

## Reference

* [Terraform-Provider-Alicloud Github](https://github.com/aliyun/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://registry.terraform.io/providers/aliyun/alicloud/latest/docs)

