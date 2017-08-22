#  Application Monitoring
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS. 


## Collect telemetry about search times
In the file /Controllers/SearchController.cs in method Index() provide these lines of code:

```
// start timer
var startTime = System.DateTime.Now;

// run search
var result = await _search.Search(q);

// compute time
var measurements = new Dictionary<string, double>()
    {
       {"SearchTimeInMilliseconds", System.DateTime.Now.Subtract(startTime).TotalMilliseconds }
    };

// log time
_telemetry.TrackEvent("Search/Server/Run", null, measurements);

```






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


## Solve the problem with the dynamic AI app id
There are several ways to tackle the problem.
### 1. Approach - read output values of ARM template
Modify your ARM template to return the IDs as output values. Then use the task [ARM Outputs](https://marketplace.visualstudio.com/search?term=output&target=VSTS&category=All%20categories&sortBy=Relevance) from the marketplace to query those values. 


### 2. Approach - query Azure resource after creation
Query the app id dynamically in a separate build task. Store it in a variable and pass this variable into the Release Annotations task.

To query the application insights appid use this powershell command
```
$aiProps= echo (az resource show --id /subscriptions/<subscriptionId>/resourceGroups/<ResourceGroupName>/providers/microsoft.insights/components/<NameOfApplicationInsights>)

$aiId = $aiProps | ConvertFrom-Json | Select -expand properties | select AppId.value

````

To be able to run "az" commands within a powershell task, you have to login to your azure subscription first. To be able to do so you need a service principal set up. Follow the steps described [here](http://) to do so, then run this command ***first*** to login your powershell.
```
az login -u <app-id> --service-principal --tenant <tenant-id> --password <app-key>
```

After that $aiId contains the ID we're looking for. Now we have to pass it to the next step. To do so we make the value available as a variable by using VSTS authoring commands as specified [here](https://github.com/Microsoft/vsts-tasks/blob/master/docs/authoring/commands.md).

So we write the value into a new variable like this:
```
Write-Host "##vso[task.setvariable variable=gAiId;]$aiId"
```
After that we can access the value from other release tasks as we can access any other variable - by using $(gAiId). 

So the whole code required would look like this:
```
az login -u <app-id> --service-principal --tenant <tenant-id> --password <app-key>

$aiProps= echo (az resource show --id /subscriptions/<subscriptionId>/resourceGroups/<ResourceGroupName>/providers/microsoft.insights/components/<NameOfApplicationInsights>)

$aiId = $aiProps | ConvertFrom-Json | Select -expand properties | select AppId.value

Write-Host "##vso[task.setvariable variable=gAiId;]$aiId"
```