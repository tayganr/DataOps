# Lab 2 - Postman Collection
In this lab, we will create a collection of HTTP requests using Postman. These requests will demonstrate the full suite of methods available within the Form Recognizer service. For more details on the Form Recognizer API, check out the [API Reference](https://aka.ms/form-recognizer/api).

## Table of Contents
   **Steps**  
   [Step 1 - Create a Collection](#step-1---create-a-collection)  
   [Step 2 - Create a Request](#step-2---create-a-request)  
   [Step 3 - Create Remaining Requests](#step-3---create-remaining-requests)  
   
   **API's**  
   [API 1 - Train Model](#api-1---train-model)  
   [API 2 - Get Models](#api-2---get-models)  
   [API 3 - Get Model](#api-3---get-model)  
   [API 4 - Get Keys](#api-4---get-keys)  
   [API 5 - Analyze Form](#api-5---analyze-form)  
   [API 6 - Delete Model](#api-6---delete-model)  

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
   | subscription_key | To find your Form Recognizer subscription key, navigate to the resource within the Azure Portal and open **Keys** under Resource Management. |
   | shared_access_signature | This is the Shared Access Signature URI generated from the previous [environment setup lab](https://github.com/tayganr/DataOps/blob/master/labs/lab-environment-setup.md#step-4---generate-a-shared-access-signature). |
   | model_id | This can be left blank for now as we don't have a model id just yet, this will happen after we train a model. |


6. Click **Create**  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-variables.png "Collection Variables")

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## Step 2 - Create a Request
In this section we will walk through how to setup a HTTP request in Postman using the Train Model API as an example. Once complete, you will be equipped with the knowledge to continue setting up requests for the remaining API's.
1. Right-click on the collection and click **Add Request**.  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-request1.png "Add Request")

2. Provide the request a name (e.g. Train Model), a description (optional), then click **Save to Form Recognizer**.  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-request2.png "Create Request")

3. Expand the Form Recognizer collection, hover over the newly created request to reveal the ellipsis, click the button and click **Open in New Tab**.  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-request3.png "Open in New Tab")

4. In this example, we need to change the HTTP Method from GET to POST. To do this, click the arrow next to GET and select POST.  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-request-method.png "Postman HTTP Method")

5. Update the endpoint to:  
```https://{{region}}.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/train```  
**Note:** The portion of the endpoint that includes "region" surrounded by curly braces is a reference to the collection variable that we created in step 1 of this lab. This allows us to change the value of the variable in a central location and have the update propogate out to all requests within the Postman collection that make reference to it.  
   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-request-endpoint.png "Postman HTTP Endpoint")

6. Navigate to **Headers** and create the following key-value pairs:  

    | Key | Value |
    | ------------- | ------------- |
    | Content-Type | application/json |
    | Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-request-headers.png "Postman HTTP Headers")

7. As this particular HTTP request example is of type POST, we must provide some data to the API in the body of the HTTP request.  Navigate to **Body**, select **raw**, copy and paste the below JSON code snippet, and finally click **Save**.  

    ```json
    {
      "source": "{{shared_access_signature}}",
      "sourceFilter": {
        "prefix": "form",
        "includeSubFolders": true
      }
    }
    ```

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-request-body.png "Postman HTTP Body")

8. Now that our request is complete, click **Send**. This will initiate the HTTP request and subsequently return a HTTP response.  If successful, the **Status** of the response will be **200 OK**. In this example as we are using the **Train Model** API, the JSON returned includes a reference to a **modelId** as well as the list of **trainingDocuments** and their corresponding details (e.g. documentName, pages, errors, status). Copy the **modelId**.

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-request-response.png "Postman HTTP Response")

9. Navigate back to the **Edit Collection** screen, switch to **Variables**, paste the **modelId** value, click **Update**.

   ![alt text](https://github.com/tayganr/DataOps/raw/master/resources/images/img-postman-collection-modelid.png "Form Recognizer Model ID")

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## Step 3 - Create Remaining Requests
By this point, we have learnt how to setup a HTTP request within a Postman collection and train a custom Form Recognizer model. Repeat [Step 2](#step-2---create-a-request) for the remaining API's to complete your Postman collection. This will demonstrate the full suite of Form Recognizer API's (Train Model > Get Models > Get Model > Get Keys > Analyze Form > Delete Model) and heighten your understanding of how they could potentially be used programmatically with your language of choice.

Note: As we have already created a saved request for Train Model, skip to [API 2 - Get Models](#api-2---get-models).

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 1 - Train Model
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

**Sample Response**
```json
{
  "modelId": "string",
  "trainingDocuments": [
    {
      "documentName": "string",
      "pages": 0,
      "errors": [
        "string"
      ],
      "status": "success"
    }
  ],
  "errors": [
    {
      "errorMessage": "string"
    }
  ]
}
```
<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 2 - Get Models
Get information about all trained custom models.

**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Sample Response**
```json
{
  "models": [
    {
      "modelId": "string",
      "status": "created",
      "createdDateTime": "string",
      "lastUpdatedDateTime": "string"
    }
  ]
}
```

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 3 - Get Model
Get information about a model.

**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Content-Type | application/json |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Sample Response**
```json
{
  "modelId": "string",
  "status": "created",
  "createdDateTime": "string",
  "lastUpdatedDateTime": "string"
}
```

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 4 - Get Keys
Retrieve the keys that were extracted during the training of the specified model.

**HTTP Method**  
GET

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```/keys

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Sample Headers**
```json
{
  "clusters": {}
}
```

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 5 - Analyze Form
Extract key-value pairs from a given document. The input document must be of one of the supported content types - 'application/pdf', 'image/jpeg' or 'image/png'. A success response is returned in JSON.

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

**Sample Response**
```json
{
  "status": "success",
  "pages": [
    {
      "number": 0,
      "height": 0,
      "width": 0,
      "clusterId": 0,
      "keyValuePairs": [
        {
          "key": [
            {
              "text": "string",
              "boundingBox": [
                0.0
              ],
              "confidence": 0.0
            }
          ],
          "value": [
            {
              "text": "string",
              "boundingBox": [
                0.0
              ],
              "confidence": 0.0
            }
          ]
        }
      ],
      "tables": [
        {
          "id": "string",
          "columns": [
            {
              "header": [
                {
                  "text": "string",
                  "boundingBox": [
                    0.0
                  ],
                  "confidence": 0.0
                }
              ],
              "entries": [
                [
                  {
                    "text": "string",
                    "boundingBox": [
                      0.0
                    ],
                    "confidence": 0.0
                  }
                ]
              ]
            }
          ]
        }
      ]
    }
  ],
  "errors": [
    {
      "errorMessage": "string"
    }
  ]
}
```

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>

## API 6 - Delete Model
Delete model artifacts.

**HTTP Method**  
DELETE

**Endpoint**  
https://```{{region}}```.api.cognitive.microsoft.com/formrecognizer/v1.0-preview/custom/models/```{{model_id}}```

**Headers**  

| Key | Value |
| ------------- | ------------- |
| Ocp-Apim-Subscription-Key | ```{{subscription_key}}``` |

**Sample Response**
HTTP Status Code 204

<div align="right"><a href="#lab-2---postman-collection">↥ back to top</a></div>
