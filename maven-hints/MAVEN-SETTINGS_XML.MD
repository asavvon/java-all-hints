# Overwrite LOCAL REPOSITORY
<localRepository>E:/devsetup/M2</localRepository>

# Add proxy
 <proxies>
        <proxy>
            <id>optional</id>
            <active>true</active>
            <protocol>http</protocol>
            <username>proxyuser</username>
            <password>proxypass</password>
            <host>proxy.host.net</host>
            <port>80</port>
            <nonProxyHosts>local.net|some.host.com</nonProxyHosts>
        </proxy>
</proxies>
