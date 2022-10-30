# Azure Sentinel map showing IP Geolocation of RDP bruteforce attacks

In this repository, i setup Azure Sentinal (SIEM) and connect it to a live virual machine acting as a honey pot. Sentinel map shows live RDP bruteforce attacks all around the world. I will use custom PowerShell script to look up the attackers Geolocation information and plot it on an Azure Sentinel Map.

SIEM setup described here will provide exposure on Azure portal, Azure Sentinel, Kusto Query Language (KQL) and Network Security Groups(NSG) in Azure.

## Languages Used
### Powershell

## Utilities Used
### https://ipgeolocation.io/

## Description

## Create Virtual Machine

![image](https://user-images.githubusercontent.com/8320161/197980138-37d44ef3-7583-4448-9ae1-8c05b8d476af.png)


## Create Log Analytics Workspace

<img width="956" alt="loganalytics workspace" src="https://user-images.githubusercontent.com/8320161/197982444-ae9950ed-fb1d-47dd-aea5-28243038ada8.PNG">


## Enable gathering VM logs in Microsoft defender

![image](https://user-images.githubusercontent.com/8320161/197980386-91bc8488-6d76-4b90-aa90-bd2cb8d51568.png)

![image](https://user-images.githubusercontent.com/8320161/197980479-d220d5ce-1aa0-42b3-ab9b-a65372cba19b.png)


## Connect Log analytics to VM

![image](https://user-images.githubusercontent.com/8320161/197995739-3dcba4f0-2a4b-46bf-8237-92e6a402fbe2.png)


## Setup Azure Sentinal

![image](https://user-images.githubusercontent.com/8320161/197982793-5bca6b10-9e29-4e8c-b477-78d71be42cc4.png)


## Log into VM with Remote Desktop

![image](https://user-images.githubusercontent.com/8320161/197997011-1ba86de0-6d1a-406e-bb82-3651418d522e.png)


## Turn off Firewall on VM

![image](https://user-images.githubusercontent.com/8320161/197984511-87d24840-79b6-4042-b6b5-e5d01f733f6f.png)


## Fail 1 login

![image](https://user-images.githubusercontent.com/8320161/197984714-e45f96bf-c67a-49bb-b972-8c2c9d7ba37f.png)

![image](https://user-images.githubusercontent.com/8320161/197985132-e6fa1339-022a-4932-9c71-ef9edff8ba32.png)


## Observe Event Viewer Logs in VM

![image](https://user-images.githubusercontent.com/8320161/197985237-1b44c85d-f088-4893-9926-7a4c4d7a9482.png)


## Get geolocation.io API key

### I logged into  https://ipgeolocation.io/ which provides access to their API key to get Geolocation for location of attacks.

![image](https://user-images.githubusercontent.com/8320161/197983711-e57892c3-5b06-4ba6-b51e-39a66aa6abf2.png)

<img width="960" alt="IP Geolocation" src="https://user-images.githubusercontent.com/8320161/197978714-4dd3b055-4e4b-4284-890a-c0e0186f3d1a.PNG">

## Run Script to get Geo Data of attacker

### Powershell script parses Windwos Event Log data for failed RDP attacks and third party API collects geographic information about the attacker's location

![image](https://user-images.githubusercontent.com/8320161/197985269-72a17ac7-9b0f-47f4-b4a5-fabb398e810c.png)

![image](https://user-images.githubusercontent.com/8320161/197985513-bff2ecd5-16f3-4f26-856c-e5c8bbc43fd7.png)


## Create custom log in the Log Analytics workspace (Law-honeypot) to bring geoinformation into custom log


![image](https://user-images.githubusercontent.com/8320161/197985572-e31fea6c-bf17-4c7e-bdcf-32bbe42d745d.png)

![image](https://user-images.githubusercontent.com/8320161/197985596-81ed820a-f9ae-4a85-8ccb-76d2def6444c.png)

![image](https://user-images.githubusercontent.com/8320161/197985879-00fab952-89df-42af-a109-43390813c40b.png)

![image](https://user-images.githubusercontent.com/8320161/197985928-7a446c4f-0e23-4422-ad4b-d342c1b7db90.png)

![image](https://user-images.githubusercontent.com/8320161/197985975-c95f1c97-7ef5-4ee6-ae1f-78ccb1f75bcc.png)

![image](https://user-images.githubusercontent.com/8320161/197986012-3158409a-5bc4-40d2-8e04-3c387d42bbfb.png)

![image](https://user-images.githubusercontent.com/8320161/197986358-81b5d5a2-867e-4e84-b2c9-6f3847c83311.png)


## Create custom fileds from raw custom log data

![image](https://user-images.githubusercontent.com/8320161/197986424-3f2001ad-9187-4a75-a036-9300445ba241.png)

![image](https://user-images.githubusercontent.com/8320161/197986459-b4cfe86d-69ae-4a1e-971d-57a7956014f2.png)

![image](https://user-images.githubusercontent.com/8320161/197986503-b21f639d-1c3e-4c22-b7b1-4c5d418a6d58.png)


## Setup map in Sentinel with Latitude and Logitude 

![image](https://user-images.githubusercontent.com/8320161/197987829-7d44d266-ea2b-4227-89be-34cb6b1f3617.png)

![image](https://user-images.githubusercontent.com/8320161/197987965-c1131410-ec32-4d0c-87c4-7ba7a287df5e.png)

![image](https://user-images.githubusercontent.com/8320161/197988351-521ffd23-9bee-4970-b3b6-7a8c5cbf55b6.png)


![image](https://user-images.githubusercontent.com/8320161/197988463-5d59bfd5-f735-40b3-b479-004088aa463b.png)


## World map of incoming attacks after 7 days
<img width="956" alt="world-map-after 7 days" src="https://user-images.githubusercontent.com/8320161/197992004-878ae409-abca-4817-a61a-c732480f9b0d.PNG">
