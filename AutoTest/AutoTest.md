#  Auto Test Hints
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS. 

## Add a task to run a quick perf test after deployment!
![Add a task to run a quick perf test after deployment](/AutoTest/images/autoTestQuickWebPerf.jpg)

## Add a task to run a cloud based load test!
Load test files can be created using Visual Studio 2017. You can use the loadtest files as provided. Make sure you swap the URL in the xml document.
![Add a task to run a cloud based load test](/AutoTest/images/autoTestLoad.jpg)

## Configure Load Test
Modify the task like shown below. 
* Path to test files is $(System.DefaultWorkingDirectory\YOURBUILDDEFINITIONNAME\testfiles
* Name of load test file is   LoadTest1.loadtest

![Config Load Test](/AutoTest/images/autoTestLoadConfig.jpg)



