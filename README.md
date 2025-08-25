# Pulumi Sample Component

A simple Pulumi component example using C# .NET that demonstrates how to create reusable infrastructure components.

## Overview

This project contains a custom Pulumi component called `SimpleStorageComponent` that creates:
- An Azure Resource Group
- An Azure Storage Account with Standard LRS SKU
- Proper tagging and organization

## Component Features

- **Encapsulation**: Bundles related resources together
- **Reusability**: Can be used multiple times with different configurations
- **Type Safety**: Strong typing with C# and Pulumi's type system
- **Output Properties**: Exposes useful outputs for consumption by other resources

## Usage

```csharp
var storageComponent = new SimpleStorageComponent("my-storage", new SimpleStorageComponentArgs
{
    StorageAccountName = "mystorageacct12345", // Must be globally unique
    Location = "East US",
    Tags = new InputMap<string>
    {
        ["Environment"] = "Development",
        ["Project"] = "MyProject"
    }
});
```

## Prerequisites

- [.NET 6.0 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
- [Pulumi CLI](https://www.pulumi.com/docs/get-started/install/)
- Azure CLI configured with appropriate credentials

## Getting Started

1. **Install dependencies:**
   ```bash
   dotnet restore
   ```

2. **Configure Pulumi:**
   ```bash
   pulumi login
   pulumi config set azure-native:location "East US"
   ```

3. **Deploy the stack:**
   ```bash
   pulumi up
   ```

4. **Clean up:**
   ```bash
   pulumi destroy
   ```

## Component Structure

### SimpleStorageComponent
- **Inputs:**
  - `StorageAccountName`: Required string for the storage account name
  - `Location`: Optional location (defaults to "East US")
  - `Tags`: Optional tags to apply to resources

- **Outputs:**
  - `ResourceGroup`: The created Azure Resource Group
  - `StorageAccount`: The created Azure Storage Account
  - `PrimaryEndpoint`: The primary blob endpoint URL

## Best Practices Demonstrated

- Component resource pattern for grouping related resources
- Proper use of Pulumi's input/output system
- Resource parenting for proper dependency management
- Consistent naming conventions
- Tagging strategy for resource organization

## Extending the Component

You can extend this component by:
- Adding more storage configuration options
- Including additional Azure resources (Key Vault, App Service, etc.)
- Adding validation logic for inputs
- Implementing different SKU options based on environment
