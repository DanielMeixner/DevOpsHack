#  Containers
This is not a step-by-step guide. Instead it's a collection of screenshots which will help you complete the DevOpsHack challenges.
This is on purpose: We want you to explore and play with the different options of VSTS. 

## Add a docker file
An appropriate dockerfile for your application could look like this. Just add it in the root of the WebApplication and name it "Dockerfile"
```
FROM microsoft/aspnetcore:1.0.5
WORKDIR /app
EXPOSE 80
COPY bin/Debug/netcoreapp1.0/publish /app
ENTRYPOINT ["dotnet", "PartsUnlimitedWebsite.dll"]
```

In case you have Docker installed locally first build your application for publishing.
```
dotnet publish
```
Then run the docker command to build the docker container from within the folder with the Dockerfile.
```
docker build -t partsunlimitedwebsite .
```
Then run the container
```
docker run -d -p 8080:80 partsunlimitedwebsite
```
If you run this locally it will start up your website in your container.