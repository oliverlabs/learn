The Azure managed identity is a free feature that's included with Microsoft Entra ID. You can use this feature to authenticate an identity to any Azure service that supports Microsoft Entra ID.

In this module, you explored service principals on the Azure platform. You saw how to use managed identities instead of service principals to authenticate your applications. If your code runs on a supported service, managed identities offer a more automated and secure way to manage credentials. Managed identities reduce the complexity of application authentication.

## Learn more

- [Services that support managed identities for Azure resources](/azure/active-directory/managed-identities-azure-resources/services-support-managed-identities). In addition to a list of supporting services, this article also provides information about region availability and configuration options.
- [Getting started on integrating Microsoft Entra ID with applications](/azure/active-directory/manage-apps/plan-an-application-integration).
- [Getting started on managing service principals by using C#](https://azure.microsoft.com/resources/samples/aad-dotnet-manage-service-principals/).
- [Create an Azure service principal by using the Azure CLI](/cli/azure/create-an-azure-service-principal-azure-cli).
- [Application and service principal objects in Microsoft Entra ID](/azure/active-directory/develop/app-objects-and-service-principals).
- [Service-to-service authentication to Azure Key Vault using .NET](/azure/key-vault/service-to-service-authentication).
- [Documentation for DefaultAzureCredential](https://github.com/Azure/azure-sdk-for-net/blob/master/sdk/identity/Azure.Identity/README.md#defaultazurecredential).
