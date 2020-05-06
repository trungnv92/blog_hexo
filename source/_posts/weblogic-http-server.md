---
title: Managing HTTP Sessions in a Cluster – In memory replication type
date: 2020-04-25 15:14:43
categories:
- coding
tags:
- Weblogic
- Oracle
---
## Một số lưu ý khi cấu hình Http Sesssion trong Weblogic Cluster.

- HTTP Session in a Cluster Weblogic gồm có 2 loại:
    1. In Memory Replication
        - Thông qua memory
    2. JDBC (Database) Replication
        - Thông qua database

- Để một ứng dụng chạy Replication Http Session thì bạn cần cấu hình ở 2 phía. 
    1. Application Server.
    2. Ứng dụng đang chạy. Cụ thể là java code 

- Điều kiện:
    1. Cài đặt Weblogic Server 12c
    2. Tạo domain và tạo 2 AppServer chạy trên 1 Cluster.
    3. Tạo một ứng dụng java nhỏ để test


- Chi tiết cấu hình như thế nào thì ở [link này nhé](https://www.oracle.com/webfolder/technetwork/tutorials/obe/fmw/wls/12c/12-ManageSessions--4478/session.htm)

- Mình chỉ có một số lưu ý khi Replication không hoạt động được:
    1. Phải thêm Cluster Address Trong Configuration Cluster (nếu chưa thêm)
        ![Cluster Address](https://1.bp.blogspot.com/-Rc-7RzK1fVo/W8lP4DepNnI/AAAAAAAANTM/T65DFUe9q7cPBRsGyH330m6mBcXkf6PxACLcBGAs/s400/cluster.png)
    2. Edit the WEB-INF/weblogic.xml file in application file .EAR or WAR
    3. Trong code java. Những object nào được lưu trong session thì phải serializable. Cách đơn giản là implements Serializable class object đó.

    **Example:**
        ``` java
            <session-descriptor>
                <persistent-store-type>replicated_if_clustered</persistent-store-type>
            </session-descriptor>
        ```
        ``` java
            class A implements Serializable{
                ...
            }
        ```

- Tạm kết