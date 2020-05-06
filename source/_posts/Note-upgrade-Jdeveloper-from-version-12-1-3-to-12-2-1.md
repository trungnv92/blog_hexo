---
title: 'Note: upgrade Jdeveloper from version 12.1.3 to 12.2.1'
date: 2020-04-25 17:08:44
tags:
- Weblogic
- Oracle
categories:
- coding
---
## Một số lưu ý khi nâng cấp bảng jdeveloper từ 12.1.3 lên 12.2.1 
1. Sử dụng java 8 thay cho java 7. Sau khi cấu hình xong, bạn phải sửa lại đường dẫn java 8 trong file 
   ```/u02/../bin/ setDomainEnv.sh``` and ```/u01/../fm1213/oracle_common/common/bin/commEnv.sh```
2. Cấu hình Replication Http Session Cho cluster 
3. Làm theo đúng hướng dẫn và sửa lại file java sử dụng session bằng cách implements Serializes
4. Bật chế độ -Dweblogic.jdbc.remoteEnabled=false->true nếu chưa bật

Happy coding. =))