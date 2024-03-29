[Lab 1 - Environment Setup](../labs/lab-environment-setup.md) > [Lab 2 - Postman Collection](../labs/lab-postman-collection.md) > [Lab 3 - Azure Functions](../labs/lab-azure-functions.md)

# Lab 1 - Environment Setup
In this lab, we will create a Form Recognizer service, an Azure Storage Account, upload some training data, and generate a Shared Access Signature URI. We recommend keeping all resources within the same resource group and the same Azure region, this will make it easier to delete at the end of the workshop and reduce latency.

## Table of Contents
   [Step 1 - Create a Form Recognizer Resource](#step-1---create-a-form-recognizer-resource)  
   [Step 2 - Create an Azure Storage Account](#step-2---create-an-azure-storage-account)  
   [Step 3 - Upload a Training Data Set](#step-3---upload-a-training-data-set)  
   [Step 4 - Generate a Shared Access Signature](#step-4---generate-a-shared-access-signature)

## Step 1 - Create a Form Recognizer Resource
1. If you have requested access to the Form Recognizer service and your access request has been approved, click the embedded Azure Portal link from the access confirmation email.  
   ![alt text](../resources/images/img-form-recognizer-public-preview.png "Form Recognizer Public Preview")

2. Once logged in to the Azure Portal, you will be presented with the Form Recognizer resource creation screen. Populate the form with the following values, click the checkbox at the bottom to confirm you have read and understood the notice, then click **Create**.
   * **Name:** This will be the name of your Form Recognizer instance.
   * **Subscription:** This is the Azure subscription where you would like to create the resource.
   * **Location:** This is the Azure region in which the resource will be deployed. The Form Recognizer Resource is currently available in two regions; (US) West US 2 and (Europe) West Europe.
   * **Pricing Tier:** There are currently two tiers; (F0) Free - includes 500 pages per month, 20 calls per minute for the recognizer API, 1 call per minute for the training API; (S0) Paid - $25 per 1,000 pages for custom models, 1 call per minute for the training API.
   * **Resource Group:** Either select an existing resource group or create a new resource group. A resource group is a logical container of Azure resources.  
        ![alt text](../resources/images/img-form-recognizer-create.png "Form Recognizer Create")
    
    Note:
    * For the purposes of this workshop, the free tier is sufficient.
    * It is recommended to select the region that is physically closest to you.

<div align="right"><a href="#lab-1---environment-setup">↥ back to top</a></div>

## Step 2 - Create an Azure Storage Account
1. In the Azure Portal, click **Create a resource**, click **Storage**, click **Storage account**.  
   ![alt text](../resources/images/img-storage-account-create1.png "Azure Storage Account Create")

2. Once presented with the Storage Account resource creation screen, populate the form with the following values, click **Review + create** and finally click **Create** at the confirmation screen.
   * **Subscription:** This is the Azure subscription where you would like to create the resource.
   * **Resource Group:** A resource group is a logical container of Azure resources. Select the same resource group as the Form Recognizer service.
   * **Storage Account Name:** The name must be unique across all existing storage account names in Azure.
   * **Location:** This is the Azure region in which the resource will be deployed. It is recommended to deploy to the same region as the Form Recognizer service.  
      ![alt text](../resources/images/img-storage-account-create2.png "Azure Storage Account Create")

<div align="right"><a href="#lab-1---environment-setup">↥ back to top</a></div>

## Step 3 - Upload a Training Data Set
1. Download the [sample forms data](../resources/data/forms.zip) and extract the contents of the zip file on to your local machine.

2. Open the Azure Portal and navigate to your Storage Account by clicking All Services > Storage > Storage accounts.  
      ![alt text](../resources/images/img-storage-account-upload1.png "Azure Storage Account")

3. Click through to open your storage account and click **Storage Explorer**. Note: This version of Storage Explorer via the Azure Portal is currently available in [public preview](https://azure.microsoft.com/en-gb/updates/storage-explorer-preview-now-available-in-azure-portal/). Alternatively, there is a client side version of the application also [available](https://azure.microsoft.com/en-us/features/storage-explorer/).  
      ![alt text](../resources/images/img-storage-account-upload2.png "Storage Explorer")

4. Right-click on Blob Containers and click **Create blob container**.  
      ![alt text](../resources/images/img-storage-account-upload3.png "Create blob container")

5. Provide the container a name (e.g. training) and click **OK**.  
      ![alt text](../resources/images/img-storage-account-upload4.png "Name blob container")

6. Perform the following steps to upload the training data set.  
   1\. Navigate to the container  
   2\. Click **Upload**  
   3\. Click the folder icon  
   4\. Select all the forms in the **training data** folder from the extracted zip file and click **Open**  
   5\. Click **Upload**  
      ![alt text](../resources/images/img-storage-account-upload5.png "Upload image")

   You should now have five images uploaded to the storage account.  
      ![alt text](../resources/images/img-storage-account-upload6.png "Uploaded images")

<div align="right"><a href="#lab-1---environment-setup">↥ back to top</a></div>

## Step 4 - Generate a Shared Access Signature
A shared access signature (SAS) is a URI that grants restricted access rights to Azure Storage resources. This will be needed by the Form Recognizer service when training a model.
1. Right-click on the blob container and select **Get Shared Access Signature**.  
      ![alt text](../resources/images/img-storage-account-sas1.png "Get Shared Access Signature")

2. Click **Create**.  
      ![alt text](../resources/images/img-storage-account-sas2.png "Create Shared Access Signature")

3. Click **Copy**. Paste this URI somewhere to be retrieved later (e.g. Notepad).  
      ![alt text](../resources/images/img-storage-account-sas3.png "Copy Shared Access Signature")

<div align="right"><a href="#lab-1---environment-setup">↥ back to top</a></div>

## Next Steps
By this point you should have the following resources available:
* Form Recognizer Cognitive Service (with endpoint and subscription key)
* Azure Storage Account (with shared access signature URI)
* [Sample Data](../resources/data/forms.zip) (1. Downloaded; 2. Extracted locally; 3. Training forms uploaded to Azure Blob Storage)

If all of these pre-steps are complete, click here to progress to [Lab 2 - Postman Collection](../labs/lab-postman-collection.md).

<div align="right"><a href="#lab-1---environment-setup">↥ back to top</a></div>
