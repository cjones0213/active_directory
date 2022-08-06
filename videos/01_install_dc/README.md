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
    - To find Interface Index

```shell
Get-NetIPAddress
```
    - To set ip for DNS

 ```shell
 Set-DnsClientServerAddress -InterfaceIndex X -ServerAddresses 192.168.xxx.xxx
 ```

 4. Add workstation to Domain

 ```
 Add-Computer -DomainName xyz.com -Credential xyz\Administrator -Force -Restart
 ```