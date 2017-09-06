#  Release Management Hints
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS. 

## Create Release Definition in VSTS
![Create Release Definition](/ReleaseManagement/images/releaseManagementAdd.jpg)

## Choose a Release Definition template in VSTS
![Choose a Release Definition template in VSTS](/ReleaseManagement/images/releaseManagementTemplate.jpg)

## Modify Release Definition Workflow in VSTS
![Modify Release Definition Workflow in VSTS](/ReleaseManagement/images/releaseManagementWorkflow.jpg)

## Add task to deploy infrastructure on Azure
![Add task to deploy infrastructure on Azure](/ReleaseManagement/images/releaseManagementRG.jpg)

## Override parameters

  ``` 
  -WebsiteName $(WebsiteName) -PartsUnlimitedServerName $(ServerName) -PartsUnlimitedServerAdminLogin AdminUser -PartsUnlimitedServerAdminLoginPassword "(ConvertTo-SecureString -String '$(AdminPassword)' -AsPlainText -Force)" -PartsUnlimitedServerAdminLoginPasswordForTest "(ConvertTo-SecureString -String '$(AdminTestPassword)' -AsPlainText -Force)" -PartsUnlimitedDBName PartsUnlimitedDB -PartsUnlimitedDBCollation SQL_Latin1_General_CP1_CI_AS -PartsUnlimitedDBEdition Basic -PartsUnlimitedHostingPlanName $(HostingPlan) -PartsUnlimitedHostingPlanSKU Standard -PartsUnlimitedHostingPlanWorkerSize 0 -EnableRules -CdnStorageAccountName $(StorageAccountName) -CdnStorageContainerName $(ContainerName) -CdnStorageAccountNameForDev $(StorageAccountName)-dev -CdnStorageContainerNameForDev $(ContainerName)-dev -CdnStorageAccountNameForStaging $(StorageAccountName)-stage -CdnStorageContainerNameForStaging $(ContainerName)-stage  
```

All parameter values like with $(something) are "variables" which to be specified in the variables tab. Make sure you choose a globally unique entry for  servername & websitename.


## Specify all parameters
Make sure both passwords are equal!

![Specify paras as parameters](/ReleaseManagement/images/releaseManagementParajpg.JPG)