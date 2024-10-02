---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "juju_jaas_access_group Resource - terraform-provider-juju"
subcategory: ""
description: |-
  A resource that represents access to a group when using JAAS.
---

# juju_jaas_access_group (Resource)

A resource that represents access to a group when using JAAS.

## Example Usage

```terraform
resource "juju_jaas_access_group" "development" {
  group_uuid       = juju_jaas_group.target-group.uuid
  access           = "member"
  users            = ["foo@domain.com"]
  groups           = [juju_jaas_group.development.uuid]
  service_accounts = ["Client-ID-1", "Client-ID-2"]
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `access` (String) Level of access to grant. Changing this value will replace the Terraform resource. Valid access levels are described at https://canonical-jaas-documentation.readthedocs-hosted.com/en/latest/reference/authorisation_model/#valid-relations
- `group_id` (String) The ID of the group for access management. If this is changed the resource will be deleted and a new resource will be created.

### Optional

- `groups` (Set of String) List of groups to grant access.
- `service_accounts` (Set of String) List of service accounts to grant access.
- `users` (Set of String) List of users to grant access.

### Read-Only

- `id` (String) The ID of this resource.

## Import

Import is supported using the following syntax:

```shell
# JAAS group access can be imported using the group UUID and access level
$ terraform import juju_jaas_access_group.development UUID:member
```