## Cinder常用命令
- 查看
- 创建/删除


- cinder service-list 查看存储服务状态
```
[root@console65 ~]# cinder service-list
+------------------+-----------------------------------------------------------+--------------------------------------+---------+-------+----------------------------+-----------------+
|      Binary      |                            Host                           |                 Zone                 |  Status | State |         Updated_at         | Disabled Reason |
+------------------+-----------------------------------------------------------+--------------------------------------+---------+-------+----------------------------+-----------------+
| cinder-scheduler |                        console65.11                       | 4746c07b-545e-45c9-8c67-4cf215dbfa30 | enabled |   up  | 2016-05-20T07:33:39.000000 |        -        |
|  cinder-volume   |                        console65.11                       | 4746c07b-545e-45c9-8c67-4cf215dbfa30 | enabled |  down |             -              |        -        |
|  cinder-volume   | console65.11@storage-009af686-9436-4a3b-8c48-6eac8f3483f8 | 4746c07b-545e-45c9-8c67-4cf215dbfa30 | enabled |   up  | 2016-05-20T07:33:34.000000 |        -        |
|  cinder-volume   | console65.11@storage-2684de03-f940-4519-8f41-daeb9616b0ca | 4746c07b-545e-45c9-8c67-4cf215dbfa30 | enabled |   up  | 2016-05-20T07:33:34.000000 |        -        |
+------------------+-----------------------------------------------------------+--------------------------------------+---------+-------+----------------------------+-----------------+
```


- cinder availability-zone-list 列出所有可用域
```
[root@console65 ~]# cinder availability-zone-list
+--------------------------------------+-----------+
|                 Name                 |   Status  |
+--------------------------------------+-----------+
| 4746c07b-545e-45c9-8c67-4cf215dbfa30 | available |
+--------------------------------------+-----------+
```


- cinder type-list 查看所有存储
```
[root@console65 ~]# cinder type-list
+--------------------------------------+----------------------------------------------+-------------+-----------+
|                  ID                  |                     Name                     | Description | Is_Public |
+--------------------------------------+----------------------------------------------+-------------+-----------+
| 42475b2c-d66d-421d-85fe-11e0575c7dca | storage-2684de03-f940-4519-8f41-daeb9616b0ca |      -      |    True   |
| 8dd996fe-c6e1-4f77-bf37-35d18a80c033 | storage-009af686-9436-4a3b-8c48-6eac8f3483f8 |      -      |    True   |
+--------------------------------------+----------------------------------------------+-------------+-----------+
```
﻿

- cinder create 创建卷
  -  [--source-volid <source-volid>]， 从另一个卷拷贝
  -  [--image-id <image-id>] [--image <image>] [--name <name>]， 从镜像创建
  -  [--volume-type <volume-type>]， 使用的存储
  -  [--availability-zone <availability-zone>]，可用域
  -  size，大小，单位G
创建空白卷：
```
[root@console65 ~]# cinder create --volume-type storage-2684de03-f940-4519-8f41-daeb9616b0ca --availability-zone  4746c07b-545e-45c9-8c67-4cf215dbfa30 1
+---------------------------------------+----------------------------------------------+
|                Property               |                    Value                     |
+---------------------------------------+----------------------------------------------+
|              attachments              |                      []                      |
|           availability_zone           |     4746c07b-545e-45c9-8c67-4cf215dbfa30     |
|                bootable               |                    false                     |
|          consistencygroup_id          |                     None                     |
|               created_at              |          2016-05-20T07:44:13.000000          |
|              description              |                     None                     |
|               encrypted               |                    False                     |
|                   id                  |     bfacf892-883a-4701-ae9d-a19d932daab0     |
|                metadata               |                      {}                      |
|            migration_status           |                     None                     |
|              multiattach              |                    False                     |
|                  name                 |                     None                     |
|         os-vol-host-attr:host         |                     None                     |
|     os-vol-mig-status-attr:migstat    |                     None                     |
|     os-vol-mig-status-attr:name_id    |                     None                     |
|      os-vol-tenant-attr:tenant_id     |       ad5b7eb919d24101a39604f9cd56d940       |
|   os-volume-replication:driver_data   |                     None                     |
| os-volume-replication:extended_status |                     None                     |
|           replication_status          |                   disabled                   |
|                  size                 |                      1                       |
|              snapshot_id              |                     None                     |
|              source_volid             |                     None                     |
|                 status                |                   creating                   |
|                user_id                |       0d4a38d812f4474088b361c189f59e8a       |
|              volume_type              | storage-2684de03-f940-4519-8f41-daeb9616b0ca |
+---------------------------------------+----------------------------------------------+
```


- cinder list 列出所有卷
```
[root@console65 ~]# cinder list
+--------------------------------------+-----------+------------------+------+------+----------------------------------------------+----------+-------------+-------------+
|                  ID                  |   Status  | Migration Status | Name | Size |                 Volume Type                  | Bootable | Multiattach | Attached to |
+--------------------------------------+-----------+------------------+------+------+----------------------------------------------+----------+-------------+-------------+
| bfacf892-883a-4701-ae9d-a19d932daab0 | available |        -         |  -   |  1   | storage-2684de03-f940-4519-8f41-daeb9616b0ca |  false   |    False    |             |
+--------------------------------------+-----------+------------------+------+------+----------------------------------------------+----------+-------------+-------------+
```


- cinder show <volume-id> 查看卷详细信息
```
[root@console65 ~]# cinder show bfacf892-883a-4701-ae9d-a19d932daab0
+---------------------------------------+--------------------------------------------------------------------------------------------------------+
|                Property               |                                                 Value                                                  |
+---------------------------------------+--------------------------------------------------------------------------------------------------------+
|              attachments              |                                                   []                                                   |
|           availability_zone           |                                  4746c07b-545e-45c9-8c67-4cf215dbfa30                                  |
|                bootable               |                                                 false                                                  |
|          consistencygroup_id          |                                                  None                                                  |
|               created_at              |                                       2016-05-20T07:44:13.000000                                       |
|              description              |                                                  None                                                  |
|               encrypted               |                                                 False                                                  |
|                   id                  |                                  bfacf892-883a-4701-ae9d-a19d932daab0                                  |
|                metadata               |                                                   {}                                                   |
|            migration_status           |                                                  None                                                  |
|              multiattach              |                                                 False                                                  |
|                  name                 |                                                  None                                                  |
|         os-vol-host-attr:host         | console65.11@storage-2684de03-f940-4519-8f41-daeb9616b0ca#storage-2684de03-f940-4519-8f41-daeb9616b0ca |
|     os-vol-mig-status-attr:migstat    |                                                  None                                                  |
|     os-vol-mig-status-attr:name_id    |                                                  None                                                  |
|      os-vol-tenant-attr:tenant_id     |                                    ad5b7eb919d24101a39604f9cd56d940                                    |
|   os-volume-replication:driver_data   |                                                  None                                                  |
| os-volume-replication:extended_status |                                                  None                                                  |
|           replication_status          |                                                disabled                                                |
|                  size                 |                                                   1                                                    |
|              snapshot_id              |                                                  None                                                  |
|              source_volid             |                                                  None                                                  |
|                 status                |                                               available                                                |
|                user_id                |                                    0d4a38d812f4474088b361c189f59e8a                                    |
|              volume_type              |                              storage-2684de03-f940-4519-8f41-daeb9616b0ca                              |
+---------------------------------------+--------------------------------------------------------------------------------------------------------+
```


- cinder delete <volume-id> 删除卷
```
[root@console65 ~]# cinder delete bfacf892-883a-4701-ae9d-a19d932daab0
Request to delete volume bfacf892-883a-4701-ae9d-a19d932daab0 has been accepted.
```


从镜像创建卷：
```
[root@console65 ~]# cinder create --volume-type storage-2684de03-f940-4519-8f41-daeb9616b0ca --availability-zone  4746c07b-545e-45c9-8c67-4cf215dbfa30 --image-id c92d44b6-d304-463d-90b2-a62ea87eedc0 1
+---------------------------------------+----------------------------------------------+
|                Property               |                    Value                     |
+---------------------------------------+----------------------------------------------+
|              attachments              |                      []                      |
|           availability_zone           |     4746c07b-545e-45c9-8c67-4cf215dbfa30     |
|                bootable               |                    false                     |
|          consistencygroup_id          |                     None                     |
|               created_at              |          2016-05-20T08:07:02.000000          |
|              description              |                     None                     |
|               encrypted               |                    False                     |
|                   id                  |     ae899c14-ad16-44f2-a0b1-aa46c821079d     |
|                metadata               |                      {}                      |
|            migration_status           |                     None                     |
|              multiattach              |                    False                     |
|                  name                 |                     None                     |
|         os-vol-host-attr:host         |                     None                     |
|     os-vol-mig-status-attr:migstat    |                     None                     |
|     os-vol-mig-status-attr:name_id    |                     None                     |
|      os-vol-tenant-attr:tenant_id     |       ad5b7eb919d24101a39604f9cd56d940       |
|   os-volume-replication:driver_data   |                     None                     |
| os-volume-replication:extended_status |                     None                     |
|           replication_status          |                   disabled                   |
|                  size                 |                      1                       |
|              snapshot_id              |                     None                     |
|              source_volid             |                     None                     |
|                 status                |                   creating                   |
|                user_id                |       0d4a38d812f4474088b361c189f59e8a       |
|              volume_type              | storage-2684de03-f940-4519-8f41-daeb9616b0ca |
+---------------------------------------+----------------------------------------------+
```
