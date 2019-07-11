# Postman Collection
In this lab, we will create a collection of HTTP requests using Postman. These requests will demonstrate the full suite of methods available within the Form Recognizer service. For more details, check out the [API Reference](https://aka.ms/form-recognizer/api).

## Table of Contents
   [Step 1 - Train Model](#step-1---train-model)  

## Step 1 - Train Model
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
