# container-quick-start
A sampling of quick and easy quickstarts for running various containers for testing or demo purposes

## Linux Containers
```bash
az container create -n cdw-dummysite-20190305 -g cdw-dummysite-20190305 -l westus2 \
  --image mcr.microsoft.com/dotnet/core/samples:aspnetapp \
  --ip-address Public --ports 80 --dns-name-label cdw-dummysite-20190305
  
az container create -n cdw-dummysite-20190305 -g cdw-dummysite-20190305 -l westus2 \
  --image ubuntu --command-line "tail -f /dev/null"
```

## Windows Server 2016 Containers
```bash
az container create -n cdw-winaci-20190307 -g cdw-winaci-20190307 -l westus2 --os-type Windows \ 
  --image mcr.microsoft.com/dotnet/core/samples:aspnetapp-nanoserver-sac2016 \
  --ip-address Public --ports 80 --dns-name-label cdw-winaci-20190307
```

## Load Testing
```bash
az container create -g cdw-loadtest-20190313 -n loadtest \
  --image bunchjesse/loadtest --restart-policy Never \
  -e REQUESTS_PER_SECOND=100 URL=https://cdw-appinsights-20190313.azurewebsites.net DURATION=60
```

## Build Agents
```bash
az container create -g cdw-containerbuildagent-20190108-rg -n cdw-containerbuildagent-20190108 \
  --image mcr.microsoft.com/azure-pipelines/vsts-agent:latest --restart-policy OnFailure \
  --environment-variables VSTS_ACCOUNT=<<YOUR_TENANT>> VSTS_TOKEN=<<YOUR_TOKEN>>
```

## Ubuntu Linux
```bash
docker run -it --rm ubuntu
```

## Certbot
[Read More Here](https://github.com/cwiederspan/letsencrypt-utils)

## SQL Server

[Read this article](http://tattoocoder.com/open-source-tools-for-sql-server-on-linux-2/)

```bash
az container create \
    --name my-sqlserver-20190411 \
    --resource-group my-sqlserver-20190411 \
    --location westus \
    --image mcr.microsoft.com/mssql/server \
    --ports 1433 \
    --vnet aci_vnet1 \
    --vnet-address-prefix 10.0.0.0/16 \
    --subnet aci_subnet1 \
    --subnet-address-prefix 10.0.0.0/24 \
    --environment-variables ACCEPT_EULA=Y SA_PASSWORD=dUmmyP@ssw0rd
```
