# Environment Setup
In this lab, you will create a Form Recognizer service and an Azure Storage Account. We recommend keeping both in a new and unique resource group, this will make it easier to delete at the end of the workshop.

## Step 1 - Create a Form Recognizer Resource
1. If you have requested access to the Form Recognizer service and your access request has been approved, click the embedded Azure Portal link from the access confirmation email.

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-form-recognizer-public-preview.png "Form Recognizer Public Preview")

2. Once logged in, you will be presented with the Form Recognizer resource creation screen. Populate the form with the following values, click the checkbox to confirm you have read and understood the notice, and click **Create**.
   * **Name:** This will be the name of your Form Recognizer instance.
   * **Subscription:** This is the Azure subscription where you would like to create the resource.
   * **Location:** This is the Azure region in which the resource will be deployed. The Form Recognizer Resource is currently available in two regions; (US) West US 2 and (Europe) West Europe.
   * **Pricing Tier:** There are currently two tiers; (F0) Free - includes 500 pages per month, 20 calls per minute for the recognizer API, 1 call per minute for the training API; (S0) Paid - $25 per 1,000 pages for custom models, 1 call per minute for the training API.
   * **Resource Group:** Either select an existing resource group or create a new resource group. A resource group is a logical container of Azure resources.


        ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-form-recognizer-create.png "Form Recognizer Create")
    
    Note:
    * For the purposes of this workshop, the free tier is sufficient.
    * It is recommended to select the region that is physically closest to you.

## Step 2 - Create an Azure Storage Account
1. In the Azure Portal, click **Create a resource**, click **Storage**, click **Storage account**.

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-storage-account-create1.png "Azure Storage Account Create")

2. Once presented with the Storage Account resource creation screen, populate the form with the following values and click **Review + create**.
   * **Subscription:** This is the Azure subscription where you would like to create the resource.
   * **Resource Group:** A resource group is a logical container of Azure resources. Select the same resource group as the Form Recognizer service.
   * **Storage Account Name:** The name must be unique across all existing storage account names in Azure.
   * **Location:** This is the Azure region in which the resource will be deployed. It is recommended to deploy to the same region as the Form Recognizer service.

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-storage-account-create2.png "Azure Storage Account Create")