# CST8912 Lab 3

**Student Name**: Collin MacLeod
**Student ID**: macl0379
**Course**: CST8912 Cloud Solutions Architecture
**Semester**: Fall 2026

## Introduction

This Lab is designed to explore storage accounts and containers. Through creating and configuring a storage account, you learn how different access tiers are used and what redundancy options are available. We explore access a blob through the internet and what is required to gain access. Finally we look at Lifecycle Management Rules which allow for powerful automations within your storage container.

## Screenshots with Analysis

### Storage Accounts with Redundancy

Locally redundant storage is the cheapest option available for redundancy. Storing backups in the same region means that recovery against corruption is satisfied but not against physical failures. Floods, fires, power outages or any other reason that might make a single data center unavailable or damaged could whip out your data. This should only be used when non critical data, there are region requirements for the data or when other options are cost prohibitive. This is where making things geo-redundant is imperative for critical information. Taking your data beyond the potential for a catastrophic event of a single area by storing it in a different region means that data can be properly secured. If there are no prohibiting reasons, this is the best choice for storage.

The configuration of the storage will also be affected by the nature of the data stored. Hot, Cool and Cold data can easily be changed into Frequent, Irregular and Rarely. If you are in need of constant access to the files stored, you should configure the account to be Hot so it can be accessed through simple transactions such as products in a catalogue. Cool data storage should be used for data that is used maybe monthly such as weekly progress report or server backups that will become obsolete as your application continues to run. For long term storage Cold is the most cost effective but the least accessible. This means that storing things such as long term financials that can be requested but are not available immediately. This configuration allows important but not used to be stored in a cost effective manner


Storage account with GRS and Hot access tier - Potentially for customer account data
![Storage Container with GRS and access tier Hot](Screenshots/Storage%20Account%20-%20GRS+Hot.png)


Storage account with LRS and access tier Cool - Potentially used for financial reports that are required to stay in a given region
![Storage account with LRS and access tier Cool](Screenshots/Storage%20Account%20-%20LRS%20+%20Cool.png)


### File Access

File access is secure whether items inherit Hot, Cool or Cold configurations. Even with Hot access, tokens are required to access data even if you have the exact destination of the file. These tokens are able to take a high number of configuration but one of the more important features is time constraints. Giving time period for access greatly reduces the risk of security concerns of urls floating around.


Storage Container with file and inherited Hot configuration
![Storage Container with file and inherited Hot configuration](Screenshots/Container%20w:%20File.png)


Access Not Permitted trying to access file with blob URL
![Access Not Permitted trying to access file with blob URL](Screenshots/Access%20not%20Permitted.png)


Access with SAS URL
![Access with SAS URL](Screenshots/Access%20w:%20SAS.png)


### Life Cycle Management

Lifecycle Management rules are a useful automation tool for data management. It allows you to move, delete or restore data with a high degree of specificity. This means you can closely manage and monitor the use and cost of your data storage. The example from this lab is a classic use of the tool ensuring data that is not used moves to the Cool tier when it goes unused. The reverse of this could be another example of good use. If a safety compliance document is sent straight to cool storage but needs to be used for an annual report it can be moved to a hot storage for 5 days after it has been accessed in Cool or Cold storage.


Lifecycle Management Rule moving blobs to Cool storage after 15 days of no use
![Lifecycle Management Rule moving blobs to Cool storage after 15 days of no use](Screenshots/Lifecycle%20Management%20Rule.png)


### Cleanup

Resource Group Deletion Successful
![Resource Group Deletion Successful](Screenshots/Cleanup%20verification.png)


## Reflections

Storage is Azure is a very powerful tool that can take a wide range of configurations. The innate ability to have data geo-redundantly stored is massive when compared to the associated cost that would be required if these were to be managed server centers. With the data centers that the cloud is run on you also benefit from the economics of quantity where larger data stores are better priced because there is so much available. When you look at a massive store of data that would come with the business of an enterprise size and ensure the automation of data management to be critical from both data security requirement needs and fiscal realities. Being able to put data in lower, less accessible tiers you are able to save which is another feature a local data storage center simply can't do because operating costs remain the same regardless of occupancy.
