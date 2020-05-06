---
title: How to add JMX to Weblogic 12c
date: 2020-04-25 16:52:00
tags:
- Weblogic
- Oracle
categories:
- coding
---
1. Stop Admin Weblogic
2. Open and Edit file setDomainEnv.sh
  
    ```java
       JAVA_OPTIONS="${JAVA_OPTIONS} 
        -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=8888 
        -Dcom.sun.management.jmxremote.ssl=false
        -Dcom.sun.management.jmxremote.authenticate=false"
        export JAVA_OPTIONS

        JAVA_OPTIONS="${JAVA_OPTIONS}"
        export JAVA_OPTIONS
        
        if [ "$SERVER_NAME" == "AdminServer" ]
        then
                JAVA_OPTIONS="${JAVA_OPTIONS} -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=8888 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.access.file=jmxremote.access -Dcom.sun.management.jmxremote.password.file=jmxremote.password"
                export JAVA_OPTIONS
        
        elif [ "$SERVER_NAME" == "mwiserver1" ]
        then
                JAVA_OPTIONS="${JAVA_OPTIONS} -Dcom.sun.management.jmxremote -Dcom.sun.management.jmxremote.port=8889 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.access.file=jmxremote.access -Dcom.sun.management.jmxremote.password.file=jmxremote.password"
                export JAVA_OPTIONS     
        fi
    ```
3. Start Weblogic again! Finish. 

Happy coding. =))
