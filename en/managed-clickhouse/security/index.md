# Identity and access management

Yandex.Cloud users can only perform operations on resources that are allowed by the roles assigned to them. If a user doesn't have any roles assigned, almost all operations are forbidden.

To allow access to the [!KEYREF mch-name] service resources (DB clusters and hosts, cluster backups, databases, and their users), assign the user the appropriate roles from the list below. At this time, a role can only be assigned to a parent resource (folder or cloud), and the roles are inherited by nested resources.

> [!NOTE]
> 
> For more information about role inheritance, see [[!TITLE]](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance) in the [!KEYREF resmgr-full-name] documentation.

## Assigning roles

To assign a role to a user:

[!INCLUDE [grant-role-console](../../_includes/grant-role-console.md)]

## Roles

The list below shows all roles that are considered when verifying access rights in the [!KEYREF mch-name] service.

### Service roles

_Service roles_ are roles that allow access to the resources of a particular service.

[!INCLUDE [cloud-roles](../../_includes/cloud-roles.md)]

### Common roles

You can assign common roles to any resource in any service.

#### [!KEYREF roles-viewer]

A user with the `[!KEYREF roles-viewer]` can view information about resources. For example, they can view a list of hosts or obtain information about a DB cluster.

#### [!KEYREF roles-editor]

A user with the `[!KEYREF roles-editor]` can manage any resources. For example, they can create a DB cluster, and create or delete a host in a cluster.

In addition, the `[!KEYREF roles-editor]` role includes all permissions of the `[!KEYREF roles-viewer]` role.

#### [!KEYREF roles-admin]

A user with the `[!KEYREF roles-admin]` role can manage access rights to resources. For example, they can allow other users to create DB clusters or view information about them.

In addition, the `[!KEYREF roles-admin]` role includes all permissions of the role of `[!KEYREF roles-editor]`.

