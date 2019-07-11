# Postman Collection
In this lab, we will create a collection of HTTP requests using Postman. These requests will demonstrate the full suite of methods available within the Form Recognizer service. For more details, check out the [API Reference](https://aka.ms/form-recognizer/api).

## Table of Contents
   [Step 1 - Train Model](#step-1---train-model)  

## Step 1 - Train Model
**HTTP Method**  
<span style="color:#FFB400">POST</span>

**Endpoint**  
https://<span style="color:#F2774A">{{region}}</span>.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/train

**Headers**
| Key  | Value |
| ------------- | ------------- |
| Content-Type  | application/json  |
| Ocp-Apim-Subscription-Key  | <span style="color:#F2774A">{{subscription_key}}</span>  |

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