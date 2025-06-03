# Play.Catalog

Play Economy Catalog microservice


# Create and publish package
### For Windows (PowerShell): 
```powershell 
$version="1.0.2"
$owner="mfdotnetmicroservices"
$gh_pat="[PAT HERE]"

dotnet pack src\Play.Catalog\ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=https://github.com/$owner/play.catalog -o ..\packages

dotnet nuget push ..\packages\Play.Catalog.$version.nupkg --api-key $gh_pat --source "github"

```

### For macOS
```bash
version="1.0.2"
owner="mfdotnetmicroservices"
gh_pat="[PAT HERE]"

dotnet pack src/Play.Catalog/ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=RepositoryUrl=https://github.com/$owner/play.catalog -o ../packages

dotnet nuget push ../packages/Play.Catalog.${version}.nupkg --api-key ${gh_pat} --source "github"
```



# Create and publish Contracts package

### For Windows (PowerShell): 
```powershell 
$version="1.0.2"
$owner="mfdotnetmicroservices"
$gh_pat="[PAT HERE]"

dotnet pack src\Play.Catalog.Contracts\ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=https://github.com/$owner/play.catalog -o ..\packages

dotnet nuget push ..\packages\Play.Catalog.Contracts.$version.nupkg --api-key $gh_pat --source "github"

```


### For macOS
```bash
version="1.0.2"
owner="mfdotnetmicroservices"
gh_pat="[PAT HERE]"

dotnet pack src/Play.Catalog.Contracts/ --configuration Release -p:PackageVersion=$version -p:RepositoryUrl=RepositoryUrl=https://github.com/$owner/play.catalog -o ../packages

dotnet nuget push ../packages/Play.Catalog.Contracts.${version}.nupkg --api-key ${gh_pat} --source "github"
```

;P