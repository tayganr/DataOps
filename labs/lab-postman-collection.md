# Postman Collection
In this lab, we will create a collection of HTTP requests using Postman. These requests will demonstrate the full suite of methods available within the Form Recognizer service. For more details, check out the [API Reference](https://aka.ms/form-recognizer/api).

## Table of Contents
   [Step 1 - Train Model](#step-1---train-model)  

## Step 1 - Create a Collection
1. Open Postman
2. Click **New Collection**  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-create.png "Create a Collection")
3. Provide the collection a name (e.g. Form Recognizer)
4. Navigate to **Variables**
5. Create the following variables with their corresponding values:  
   | VARIABLE | VALUE |
   | ------------- | ------------- |
   | region | This will be ```westus2``` or ```westeurope``` depending on which location you selected when creating the Form Recognizer service. |
   | subscription_key | To find your Form Recognizer subscription key, navigate to the resource within the Azure Portal and open **Keys** under Resource Management |
   | shared_access_signature | This is the Shared Access Signature URI generated from the previous [environment setup lab](https://github.com/tayganr/DataOps/blob/master/labs/lab-environment-setup.md#step-4---generate-a-shared-access-signature). |
   | model_id | This can be left blank for now as we don't have a model id just yet, this will happen after we train a model. |
6. Click **Create**

![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-variables.png "Collection Variables")

## Step 2 - Create a Request (Train Model)
1. Right-click on the collection and click **Add Request**  
![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-request.png "Add Request")

## Step 1 - Train Model
Create and train a custom model. The train request must include a source parameter that is either an externally accessible Azure Storage blob container Uri (preferably a Shared Access Signature Uri) or valid path to a data folder in a locally mounted drive.

**HTTP Method**  
POST

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/train

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Content-Type | application/json |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Body**
```json
{
  "source": "{{shared_access_signature}}",
  "sourceFilter": {
    "prefix": "form",
    "includeSubFolders": true
  }
}
```

## Step 1 - Get Models
**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

## Step 1 - Get Model
**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Content-Type | application/json |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

## Step 1 - Get Keys
**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```/keys

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

## Step 1 - Analyze Form
**HTTP Method**  
POST

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```/analyze

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Content-Type | image/png |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Body**  
Insert image of Body > Binary > analyze_form.png  

## Step 1 - Delete Model
**HTTP Method**  
DELETE

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |
