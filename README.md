# container-quick-start
A sampling of quick and easy quickstarts for running various containers for testing or demo purposes

## Linux Containers
```bash
az container create -n cdw-dummysite-20190305 -g cdw-dummysite-20190305 -l westus2 \
  --image mcr.microsoft.com/dotnet/core/samples:aspnetapp \
  --ip-address Public --ports 80 --dns-name-label cdw-dummysite-20190305
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
