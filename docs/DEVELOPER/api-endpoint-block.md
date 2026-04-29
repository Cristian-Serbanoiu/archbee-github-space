---
title: API Endpoint
slug: api-endpoint-blocks
icon: {"faIcon":"fa-solid fa-plug"}
docTags: Revenge
createdAt: Tue Apr 28 2026 13:00:08 GMT+0000 (Coordinated Universal Time)
updatedAt: Wed Apr 29 2026 08:19:15 GMT+0000 (Coordinated Universal Time)
---

:::ApiMethodV2
```json
{
  "name": "Get Cakes 1",
  "method": "GET",
  "url": "https://api.cakes.com",
  "description": "Get a cake by its ID",
  "tab": "examples",
  "examples": {
    "languages": [
      {
        "id": "rMPOQU_1kHGiTPpScUYdI",
        "language": "javascript",
        "code": "var myHeaders = new Headers();\nmyHeaders.append(\"Accept\", \"application/json\");\nmyHeaders.append(\"Content-Type\", \"application/json\");\n\nvar raw = JSON.stringify({\n   \"id\": \"string\"\n});\n\nvar requestOptions = {\n   method: 'GET',\n   headers: myHeaders,\n   body: raw,\n   redirect: 'follow'\n};\n\nfetch(\"https://api.cakes.com\", requestOptions)\n   .then(response => response.text())\n   .then(result => console.log(result))\n   .catch(error => console.log('error', error));",
        "customLabel": ""
      }
    ],
    "selectedLanguageId": "rMPOQU_1kHGiTPpScUYdI"
  },
  "results": {
    "languages": [
      {
        "id": "SUm_D6qiRs0Y1D1Y1lZOy",
        "language": "200",
        "code": "{\n  \"name\": \"Cake's name\",\n}",
        "customLabel": ""
      },
      {
        "id": "sckvSeRYTZ93lmHKVedre",
        "language": "404",
        "code": "{\n  \"message\": \"Ain't no cake like that.\"\n}",
        "customLabel": ""
      }
    ],
    "selectedLanguageId": "SUm_D6qiRs0Y1D1Y1lZOy"
  },
  "request": {
    "pathParameters": [],
    "queryParameters": [],
    "headerParameters": [],
    "formDataParameters": [],
    "bodyDataParameters": [
      {
        "name": "id",
        "kind": "required",
        "type": "string",
        "description": "ID of the cake to get"
      }
    ]
  },
  "currentNewParameter": {
    "label": "Body Parameter",
    "value": "bodyDataParameters"
  },
  "hasTryItOut": false
}
```
:::

de la mihai
