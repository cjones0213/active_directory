# 01 Installing the Domain Controller

1. Use `sconfig` to :
    - Change the hostname
    - Change the IP address to static
    - Change the DNS server to our own IP address

2. Install the Active Directory Windows Feature

```shell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
```
```shell
Import-Module ADDSDeployment
```
```shell
Install-ADDSForest
```
- Set DomainName

3. Set Domain Controller DNS and Set Workstation DNS

```shell
Get-NetIPAddress
```

- To find Interface Index X

 ```shell
 Set-DnsClientServerAddress -InterfaceIndex X -ServerAddresses 192.168.xxx.xxx
 ```
- To set ip for DNS

 4. Add workstation VM to Domain

 ```
 Add-Computer -DomainName xyz.com -Credential xyz\Administrator -Force -Restart
 ```