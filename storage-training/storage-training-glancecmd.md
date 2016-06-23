- 从文件创建镜像
```
[root@console65 ~]# glance image-create --container-format bare --disk-format qcow2 --file test.img --name test 
+------------------+----------------------------------------------------------------------------------+
| Property         | Value                                                                            |
+------------------+----------------------------------------------------------------------------------+
| checksum         | 5789e2a5cabb3007171a45a06e86936f                                                 |
| container_format | bare                                                                             |
| created_at       | 2016-05-20T08:02:35Z                                                             |
| disk_format      | qcow2                                                                            |
| id               | c92d44b6-d304-463d-90b2-a62ea87eedc0                                             |
| locations        | [{"url": "file:///opt/glance/images/c92d44b6-d304-463d-90b2-a62ea87eedc0",       |
|                  | "metadata": {}}]                                                                 |
| min_disk         | 0                                                                                |
| min_ram          | 0                                                                                |
| name             | test                                                                             |
| owner            | ad5b7eb919d24101a39604f9cd56d940                                                 |
| protected        | False                                                                            |
| size             | 197120                                                                           |
| status           | active                                                                           |
| tags             | []                                                                               |
| updated_at       | 2016-05-20T08:02:35Z                                                             |
| virtual_size     | None                                                                             |
| visibility       | private                                                                          |
+------------------+----------------------------------------------------------------------------------+
```


- 查看镜像列表
```
[root@console65 ~]# glance image-list
+--------------------------------------+------+
| ID                                   | Name |
+--------------------------------------+------+
| c92d44b6-d304-463d-90b2-a62ea87eedc0 | test |
+--------------------------------------+------+
```


- 查看镜像详细信息
```
[root@console65 ~]# glance image-show c92d44b6-d304-463d-90b2-a62ea87eedc0
+------------------+----------------------------------------------------------------------------------+
| Property         | Value                                                                            |
+------------------+----------------------------------------------------------------------------------+
| checksum         | 5789e2a5cabb3007171a45a06e86936f                                                 |
| container_format | bare                                                                             |
| created_at       | 2016-05-20T08:02:35Z                                                             |
| disk_format      | qcow2                                                                            |
| id               | c92d44b6-d304-463d-90b2-a62ea87eedc0                                             |
| locations        | [{"url": "file:///opt/glance/images/c92d44b6-d304-463d-90b2-a62ea87eedc0",       |
|                  | "metadata": {}}]                                                                 |
| min_disk         | 0                                                                                |
| min_ram          | 0                                                                                |
| name             | test                                                                             |
| owner            | ad5b7eb919d24101a39604f9cd56d940                                                 |
| protected        | False                                                                            |
| size             | 197120                                                                           |
| status           | active                                                                           |
| tags             | []                                                                               |
| updated_at       | 2016-05-20T08:02:35Z                                                             |
| virtual_size     | None                                                                             |
| visibility       | private                                                                          |
+------------------+----------------------------------------------------------------------------------+
```

