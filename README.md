# hikvision2nodered
Receiving events from Hikvision devices in NodeRed
Only notification subscription is used.

Unfortunately I couldn't get XML directly, NodeRed doesn't accept the format
General idea of ​​this approach (many thanks to the author) - https://flows.nodered.org/flow/12569b0e9e05c773ce54aa923f68c110


1. Setting up Hik device /ISAPI/Event/notification/httpHosts/1  to send events
   Example:
           <?xml version="1.0" encoding="UTF-8"?>
        <HttpHostNotification version="2.0" xmlns="http://www.hikvision.com/ver20/XMLSchema">
        <id>1</id>
        <url>/cam</url>
        <protocolType>HTTP</protocolType>    
        <parameterFormatType>XML</parameterFormatType>             // <- Impossible to change
        <addressingFormatType>ipaddress</addressingFormatType>
        <ipAddress>192.168.168.254</ipAddress>
        <portNo>8080</portNo>
        <userName></userName>
        <httpAuthenticationMethod>none</httpAuthenticationMethod>
        </HttpHostNotification>
        
2. Сheck on the NodeRed host side
       sudo tcpdump -i [interface name] port 8080 -A

3. Create flow
   Example:
   https://github.com/ak77m/hikvision2nodered/blob/main/Sample.json
    

