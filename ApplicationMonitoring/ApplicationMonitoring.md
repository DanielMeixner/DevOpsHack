#  Application Monitoring
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS. 


## Install Release Annotations for your account
Install the required extension from the marketplace [here](https://marketplace.visualstudio.com/items?itemName=ms-appinsights.appinsightsreleaseannotations) .
![Install the required extension from the marketplace.](/ApplicationMonitoring/images/ApplicationMonitoringInstallFromMarketplace.JPG)


## Add the task
Add the Task. Find the Key in the app id in the Azure portal. Have a look at task groups to avoid recurring work when working with differnt environments. Also check the variables to make environment specific settings.
![Add release annotations task](/ApplicationMonitoring/images/ApplicationMonitoringAnnotationsTask.jpg)

## Create an availability test in the portal
In the portal look for the AI component for your Dev environment and add an availabiltiy test. Explore the settings!
![Add availability test](/ApplicationMonitoring/images/ApplicationMonitoringAvailabilityTest.jpg)

## Create a Work Item in the portal
Starting in your application insights view in Azure Portal go and follow down the Page View metric until you find the requests. Choose one and look for the "New Work Item" button. Configure it for your account for first time usage.
![Create a Work Item in Azure Portal ](/ApplicationMonitoring/images/ApplicationMonitoringNewWorkItem.jpg)

## Modify your VSTS Dashboard
Right click the icon in the lower right corner to start modifying your dashboard. Add the Azure Application Insights Widget. If not available get it from the marketplace. To find out how to modify it, follow the "Learn more" link.

![Modify dashboard ](/ApplicationMonitoring/images/ApplicationMonitoringDashboardMod.jpg)


![Add AI widget ](/ApplicationMonitoring/images/ApplicationMonitoringAIWidget.jpg)



