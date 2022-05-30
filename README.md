# jjazure-web-dotnet-draft

This repo describes how to Draft for AKS

Docs
- https://docs.microsoft.com/en-us/azure/aks/draft

## Create project

```powershell
dotnet new mvc --name jjweb

dotnet tool install --global dotnet-gitignore --version 1.2.1
dotnet-gitignore
```

## Create K8s artifacts

```powershell
az aks draft create
```

## Configure GitHub Actions

Prereq
- Must install GH CLI first
- create Azure resource group

```powershell
choco install gh

az aks draft setup-gh

az aks draft generate-workflow
```