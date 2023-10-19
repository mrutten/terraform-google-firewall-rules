# Table of Contents

- [Table of Contents](#table-of-contents)
- [Introduction](#introduction)
  - [Requirements](#requirements)
  - [Providers](#providers)
  - [Modules](#modules)
  - [Resources](#resources)
  - [Inputs](#inputs)
  - [Outputs](#outputs)

# Introduction

This is a Terraform module that creates a number of firewall rules for a VPC.

## Requirements

| Name                                                                      | Version  |
| ------------------------------------------------------------------------- | -------- |
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.3.0 |
| <a name="requirement_google"></a> [google](#requirement\_google)          | 5.2.0    |

## Providers

| Name                                                       | Version |
| ---------------------------------------------------------- | ------- |
| <a name="provider_google"></a> [google](#provider\_google) | 5.2.0   |

## Modules

No modules.

## Resources

| Name                                                                                                                                           | Type     |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| [google_compute_firewall.rules_ingress_egress](https://registry.terraform.io/providers/hashicorp/google/5.2.0/docs/resources/compute_firewall) | resource |

## Inputs

| Name                                                                        | Description                                                                   | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | Default | Required |
| --------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------- | :------: |
| <a name="input_egress_rules"></a> [egress\_rules](#input\_egress\_rules)    | List of egress rules. This will be ignored if variable 'rules' is non-empty.  | <pre>list(object({<br>    name                    = string<br>    description             = optional(string, null)<br>    priority                = optional(number, null)<br>    destination_ranges      = optional(list(string), [])<br>    source_ranges           = optional(list(string), [])<br>    source_tags             = optional(list(string))<br>    source_service_accounts = optional(list(string))<br>    target_tags             = optional(list(string))<br>    target_service_accounts = optional(list(string))<br><br>    allow = optional(list(object({<br>      protocol = string<br>      ports    = optional(list(string))<br>    })), [])<br>    deny = optional(list(object({<br>      protocol = string<br>      ports    = optional(list(string))<br>    })), [])<br>    log_config = optional(object({<br>      metadata = string<br>    }))<br>  }))</pre> | `[]`    |    no    |
| <a name="input_ingress_rules"></a> [ingress\_rules](#input\_ingress\_rules) | List of ingress rules. This will be ignored if variable 'rules' is non-empty. | <pre>list(object({<br>    name                    = string<br>    description             = optional(string, null)<br>    priority                = optional(number, null)<br>    destination_ranges      = optional(list(string), [])<br>    source_ranges           = optional(list(string), [])<br>    source_tags             = optional(list(string))<br>    source_service_accounts = optional(list(string))<br>    target_tags             = optional(list(string))<br>    target_service_accounts = optional(list(string))<br><br>    allow = optional(list(object({<br>      protocol = string<br>      ports    = optional(list(string))<br>    })), [])<br>    deny = optional(list(object({<br>      protocol = string<br>      ports    = optional(list(string))<br>    })), [])<br>    log_config = optional(object({<br>      metadata = string<br>    }))<br>  }))</pre> | `[]`    |    no    |
| <a name="input_network_name"></a> [network\_name](#input\_network\_name)    | Name of the network this set of firewall rules applies to.                    | `string`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | n/a     |   yes    |
| <a name="input_project_id"></a> [project\_id](#input\_project\_id)          | Project id of the project that holds the network.                             | `string`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | n/a     |   yes    |

## Outputs

| Name                                                                                                                              | Description                                         |
| --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| <a name="output_firewall_rules_ingress_egress"></a> [firewall\_rules\_ingress\_egress](#output\_firewall\_rules\_ingress\_egress) | The created firewall ingress/egress rule resources. |
