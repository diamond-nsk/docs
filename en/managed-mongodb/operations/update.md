# Changing cluster settings

After creating a cluster, you can:

- [Change the host class](#change-resource-preset).
- [Increase the storage size](#change-disk-size) (available only for network storage, `network-hdd` and `network-nvme`).
- [Configure the servers](#change-mongod-config) [!KEYREF MG] as described in the [documentation [!KEYREF MG]](https://docs.mongodb.com/v3.6/reference/configuration-options/).

## Change the host class {#change-resource-preset}

---

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

To change the [host class](../concepts/instance-types.md) for the cluster:

1. View the description of the CLI's update cluster command:

   ```
   $ [!KEYREF yc-mdb-mg] cluster update --help
   ```

1. Request a list of available host classes (the `ZONES` column specifies the availability zones where you can select the appropriate class):

   ```
   $ [!KEYREF yc-mdb-mg] resource-preset list
   
   +-----------+--------------------------------+-------+--------------+
   |    ID     |              ZONES             | CORES |    MEMORY    |
   +-----------+--------------------------------+-------+--------------+
   | s1.nano   | ru-central1-a, ru-central1-b,  |     1 |   4294967296 |
   |           | ru-central1-c                  |       |              |
   | s1.micro  | ru-central1-a, ru-central1-b,  |     2 |   8589934592 |
   |           | ru-central1-c                  |       |              |
   | ...                                                               |
   +-----------+--------------------------------+-------+--------------+
   ```

1. Specify the class in the update cluster command:

   ```
   $ [!KEYREF yc-mdb-mg] cluster update <cluster name>
        --mongod-resource-preset <class ID>
   ```

   [!KEYREF mmg-short-name] will run the update host class command for the cluster.

**[!TAB API]**

You can change the cluster [host class](../concepts/instance-types.md) using the API's [update](../api-ref/Cluster/update.md) method: pass the appropriate values in the request parameter `configSpec.mongodbSpec_3_6.mongod.config.resourcePresetId`.

To request a list of supported values, use the [list](../api-ref/ResourcePreset/list.md) method for the `ResourcePreset` resources.

---

## Increasing the storage size {#change-disk-size}

---

**[!TAB CLI]**

[!INCLUDE [cli-install](../../_includes/cli-install.md)]

[!INCLUDE [default-catalogue](../../_includes/default-catalogue.md)]

To increase the storage size for a cluster:

1. View the description of the CLI's update cluster command:

   ```
   $ [!KEYREF yc-mdb-mg] cluster update --help
   ```

1. Make sure the cloud's quota is sufficient to increase the storage size: open the [Quotas](https://console.cloud.yandex.ru/?section=quotas) for your cloud and check that the [!KEYREF mmg-full-name] section still has space remaining in the **space** line.

1. Make sure the required cluster is using network storage (it is not yet possible to increase the size of local storage). To do this, request information about the cluster and find the `disk_type_id` field: it should be set to `network-hdd` or `network-nvme`:

   ```
   $ [!KEYREF yc-mdb-mg] cluster get <cluster name>
   
   id: c7qkvr3u78qiopj3u4k2
   folder_id: b1g0ftj57rrjk9thribv
   ...
   config:
     mongodb_3_6:
       mongod:
         config:
           user_config: {}
         resources:
           resource_preset_id: s1.micro
           disk_size: "21474836480"
           disk_type_id: network-nvme
   ...
   ```

1. Specify the required amount of storage in the update cluster command (it must be at least as large as `disk_size` in the cluster properties):

   ```
   $ [!KEYREF yc-mdb-mg] cluster update <cluster name>
        --mongod-disk-size <storage size in GB>
   ```

   If all requirements are met, [!KEYREF mmg-short-name] runs the operation to increase the storage size.

**[!TAB API]**

You can change the storage size for a cluster using the API [update](../api-ref/Cluster/update.md) method: pass the appropriate values in the request parameter `configSpec.mongodbSpec_3_6.mongod.resources.diskSize`.

Make sure the cloud's quota is sufficient to increase the storage size: open the [Quotas](https://console.cloud.yandex.ru/?section=quotas) for your cloud and check that the [!KEYREF mmg-full-name] section still has space remaining in the **space** line.

---

## Changing [!KEYREF MG] {#change-mongod-config} settings

You can change the DBMS settings of the hosts in your cluster. All supported settings are described [in the API reference](../api-ref/Cluster/update.md).

---

**[!TAB API]**

You can change the DBMS settings for a cluster using the API [update](../api-ref/Cluster/update.md) method: pass the appropriate values in the request parameter `configSpec.mongodbSpec_3_6.mongod.config.resourcePresetId`.

---

