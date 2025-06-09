# Play.Catalog

Play Economy Catalog microservice


# Create and publish package
### For Windows (PowerShell): 
```powershell 
$version="1.0.3"
$owner="mfdotnetmicroservices"
$gh_pat="[PAT HERE]"

dotnet pack src\Play.Catalog\ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=https://github.com/$owner/play.catalog -o ..\packages

dotnet nuget push ..\packages\Play.Catalog.$version.nupkg --api-key $gh_pat --source "github"

```

### For macOS
```bash
version="1.0.3"
owner="mfdotnetmicroservices"
gh_pat="[PAT HERE]"

dotnet pack src/Play.Catalog/ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=RepositoryUrl=https://github.com/$owner/play.catalog -o ../packages

dotnet nuget push ../packages/Play.Catalog.${version}.nupkg --api-key ${gh_pat} --source "github"
```



# Create and publish Contracts package

### For Windows (PowerShell): 
```powershell 
$version="1.0.3"
$owner="mfdotnetmicroservices"
$gh_pat="[PAT HERE]"

dotnet pack src\Play.Catalog.Contracts\ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=https://github.com/$owner/play.catalog -o ..\packages

dotnet nuget push ..\packages\Play.Catalog.Contracts.$version.nupkg --api-key $gh_pat --source "github"

```


### For macOS
```bash
version="1.0.3"
owner="mfdotnetmicroservices"
gh_pat="[PAT HERE]"

dotnet pack src/Play.Catalog.Contracts/ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=RepositoryUrl=https://github.com/$owner/play.catalog -o ../packages

dotnet nuget push ../packages/Play.Catalog.Contracts.${version}.nupkg --api-key ${gh_pat} --source "github"
```




## Build the docker image
### windows (powershell)
```powershell
-beta
$env:GH_OWNER="mfdotnetmicroservices"
$env:GH_PAT="[PAT HERE]"
$acrname="playeconomyacr"
docker build --secret id=GH_OWNER --secret id=GH_PAT -t "$acrname.azurecr.io/play.catalog:$version" .
```



### macOS (bash)
```bash
$acrname="playeconomyacr"
export GH_OWNER="mfdotnetmicroservices"
export GH_PAT="[PAT HERE]"
docker build --secret id=GH_OWNER --secret id=GH_PAT -t "$acrname.azurecr.io/play.catalog:$version" .

```






## Run the docker image

### windows (powershell)
```powershell
$version="1.0.3"
docker run -it --rm -p 5009:5009 --name catalog -e MongoDbSettings__ConnectionString=mongo -e RabbitMQSettings__Host=rabbitmq --network playinfra_default play.catalog:$version  
```



## Run the docker image
### macOS (bash)
```bash
version="1.0.3"
cosmosDbConnString="[CONN STRING HERE]"
serviceBusConnString="[CONN STRING HERE]"
docker run -it --rm -p 5009:5009 --name catalog -e MongoDbSettings__ConnectionString=$cosmosDbConnString -e ServiceBusSettings__ConnectionString=$serviceBusConnString -e ServiceSettings__MessageBroker="SERVICEBUS" play.catalog:$version

```


## Publishing the Docker image
### For PC
```powershell

$acrname="playeconomyacr"
az acr login --name $acrname
docker push "$acrname.azurecr.io/play.catalog:$version"
```

### For MacOS
```bash
az acr login --name "$acrname"
docker push "$acrname.azurecr.io/play.catalog:$version"

```
