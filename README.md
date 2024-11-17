# vue-auth-app

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

# Deployment Guide for vue-auth-app

This guide provides detailed steps to deploy the `vue-auth-app` to an Azure Storage account and serve it as a static website.

## Prerequisites

- [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) installed
- Azure account

## Steps to Deploy

### 1. Log in to Azure

First, log in to your Azure account using the Azure CLI.

```sh
az login
```

### 2. Create a Resource Group

Create a resource group if you don't already have one. Replace vue-app with your desired resource group name and eastasia with your preferred region.

```sh
az group create --name vue-app --location eastasia
```

### 3. Create a Storage Account
Create a storage account. Replace vueauthapp with your desired storage account name.

```sh
az storage account create --name vueauthapp --resource-group vue-app --location eastasia --sku Standard_LRS --kind StorageV2
```

### 4. Enable Static Website Hosting
Enable static website hosting on the storage account.

```sh
az storage blob service-properties update --account-name vueauthapp --static-website --index-document index.html --404-document [404.html](http://_vscodecontentref_/0)
```

### 5. Build Your Vue.js App
Build your Vue.js app to generate the static files.

```sh
npm run build
```

### 6. Upload Your Files
Upload the generated files from the dist directory to the $web container in your storage account.

```sh
az storage blob upload-batch -d '$web' --account-name vueauthapp -s ./dist
```

### 7. Ensure All Files Are Publicly Accessible
Set the permissions for the $web container to allow public access.

```sh
az storage blob set-permission --container-name '$web' --account-name vueauthapp --public-access blob
```

### 8. Get the URL of Your Static Website
Retrieve the URL where your static website is hosted.

```sh
az storage account show --name vueauthapp --resource-group vue-app --query "primaryEndpoints.web" --output tsv
```

The output will be the URL where your static website is host https://vueauthapp.z7.web.core.windows.net