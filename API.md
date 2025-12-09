## General

This REST API is designed to manage the relationship between surveys and it's questions and responses. It provides a set of CRUD (Create, Read, Update, Delete) operations in order to manage surveys and it's associated questions and answers.

This backend and its API primarily provides server-rendered Thymeleaf views, but it also exposes a small number of REST endpoints for saving survey responses. These endpoints are intended for use by JavaScript calls or external tools (Bruno/Postman).

**Note:** This backend is not designed as a full REST API. Only the endpoints listed here are intended to be used programmatically.


## User Instructions

This API-documentation follows a single-file format for easier maintenance purposes. You can browse different sections by clicking the links below:
***
[**Surveys**](#surveys)
***
[**Questions:**](#questions)
***
[**Responses:**](#repsonses)
***

## Overview
The API is structured around three main resources: Surveys, Questions and Responses. 
- [**Surveys**](#surveys) present information of the survey and a list of questions that can be answered. Each survey also has attributes such as name, description, date of creation and starting date and ending date for responding.
- [**Questions:**](#questions) represent interactive fields for surveys. Each question has attributes like the question's type (either  text field or multiple choice via radio button), and the question's heading.
- [**Responses:**](#responses) present a list of responses to a survey or a specific question. Each response has an attribute of response's text or choice in addition of the question it's associated with.

There is a one-to-many relationship between surveys and questions, which means one survey an have multiple questions, but one question can be associated with only one survey.

There is also a many-to-one relationship between responses and questions, which means there can be multiple responses to one question, but one response can be associated wit only one question.

### Base URL

`https://kysely-spring-git-backend.2.rahtiapp.fi/api`

### Method:

`GET`

### Success Response:

Upon successful loading, the base API will return a 200 OK status code to the console and the response body contains a JSON-file of links to the API's of surveys, questions and responses. If loading fails for any reason, the API will return an appropriate error status code and message to the browser and / or console.

**Code**: `200`

**Content:** 

```
{
  "_links" : {
    "surveys" : {
      "href" : "https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys"
    },
    "questions" : {
      "href" : "https://kysely-spring-git-backend.2.rahtiapp.fi/api/questions"
    },
    "responses" : {
      "href" : "https://kysely-spring-git-backend.2.rahtiapp.fi/api/responses"
    },
    "profile" : {
      "href" : "https://kysely-spring-git-backend.2.rahtiapp.fi/api/profile"
    }
  }
}
```

### Error Response:
Browser's general error message

# Surveys

### Base URL

`https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys`

## Endpoints

### Get all surveys
Fetch all existing surveys

**Request:**

- HTTP Method: `GET`
- Endpoint: `/api/surveys`
- Request Parameters: None

**Response:**
JSON object containing an array of surveys. Each survey object includes the following fields:
- `surveyId:` The survey's automatically generated, unique identifier. (long)
- `surveyName:` The survey's name. (string)
- `surveyDesc:` The survey's description. (string)
- `createdDate:`  The survey's date of creation, generated automatically to correspond current date. (localDateTime)
- `startingDate:` Date when the survey starts accepting answers. (string)
- `endingDate:` Date when the survey stops accepting answers. (string)

**Example Response:**

```
 {
  "surveyId": 6,
  "surveyName": "Haaga-Helia TRATI - Opetuksen laatukysely",
  "surveyDesc": "Kerro, mitä mieltä olet HH IT-Tradenomin koulutusohjelman opetuksen laadusta!",
  "createdDate": "2025-12-04T11:17:39.649185",
  "startingDate": "2025-11-13",
  "endingDate": "2025-12-22",
  "questions": [
    {
      "questionId": 33,
      "questionText": "Monennenko vuoden opiskelija olet?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 34,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "radioButton",
      "options": [
        "ICT ja liiketoiminta",
        "ICT-infra ja pilvipalvelut",
        "Ohjelmistokehitys",
        "Digitaaliset palvelut"
      ]
    },
{
    "surveyId": 7,
    "surveyName": "HSL-sovelluksen toimivuus -kysely",
    "surveyDesc": "Tämä kysely kerää palautetta HSL-sovelluksen toimivuudesta ja käyttäjäkokemuksesta palvelun kehittämistä varten.",
    "createdDate": "2025-12-09T12:55:13.409984",
    "startingDate": "2025-12-09",
    "endingDate": "2025-12-30",
    "questions": [
      {
        "questionId": 55,
        "questionText": "Oletko kohdannut teknisiä ongelmia sovellusta käyttäessäsi?",
        "questionType": "radioButton",
        "options": [
          "Kyllä",
          "En"
        ]
      },
      {
        "questionId": 56,
        "questionText": "Jos vastasit kyllä, millaisia teknisiä ongelmia olet huomannut?",
        "questionType": "text",
        "options": []
      },
```

**Notes:** 
- More surveys omitted for brevity.
- `options` is an empty array for text questions and only populated for multiple-choice/radio questions.

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey not found
- `500 Internal Server Error`

***

### Get survey by id
Fetch a specific survey by its unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/api/surveys/{surveyId}`
- Path Parameters: `surveyId` (long, required): The unique identifier of the survey

**Example Request:**
`GET /api/surveys/6`

**Response:**
- Body: JSON object with the survey's details.


**Example Response:**

```
{
  "surveyId": 6,
  "surveyName": "Haaga-Helia TRATI - Opetuksen laatukysely",
  "surveyDesc": "Kerro, mitä mieltä olet HH IT-Tradenomin koulutusohjelman opetuksen laadusta!",
  "createdDate": "2025-12-04T11:17:39.649185",
  "startingDate": "2025-11-13",
  "endingDate": "2025-12-22",
  "questions": [
    {
      "questionId": 33,
      "questionText": "Monennenko vuoden opiskelija olet?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 34,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "radioButton",
      "options": [
        "ICT ja liiketoiminta",
        "ICT-infra ja pilvipalvelut",
        "Ohjelmistokehitys",
        "Digitaaliset palvelut"
      ]
    },
    {
      "questionId": 35,
      "questionText": "Opintojesi toteutusmuoto?",
      "questionType": "radioButton",
      "options": [
        "Päivätoteutus",
        "Monimuoto"
      ]
    },
    {
      "questionId": 36,
      "questionText": "Ikäsi:",
      "questionType": "radioButton",
      "options": [
        "alle 18-vuotias",
        "18-24-vuotias",
        "25-29-vuotias",
        "30-34-vuotias",
        "35 tai yli"
      ]
    },
    {
      "questionId": 37,
      "questionText": "Sukupuolesi:",
      "questionType": "radioButton",
      "options": [
        "Mies",
        "Nainen",
        "Muu",
        "En halua kertoa"
      ]
    },
    {
      "questionId": 38,
      "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
      "questionType": "text",
      "options": []
    },
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey not found: `{surveyId}`
- `500 Internal Server Error`

***

# Questions

### Base URL
`https://kysely-spring-git-backend.2.rahtiapp.fi/api/questions`

## Endpoints

### Get Questions by Survey Id
Fetch a specific survey's questions by its unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/api/surveys/{surveyId}/questions`
- Path Parameters: `{surveyId}` (long, required): The unique identifier of the survey


**Example Request:**
`GET /api/surveys/6/questions`

**Response:**
- Body: JSON array of objects with the survey's question details. No survey details included.

**Example Response:**
```
 [
  {
    "questionId": 33,
    "questionText": "Monennenko vuoden opiskelija olet?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 34,
    "questionText": "Opintojesi suuntaus?",
    "questionType": "radioButton",
    "options": [
      "ICT ja liiketoiminta",
      "ICT-infra ja pilvipalvelut",
      "Ohjelmistokehitys",
      "Digitaaliset palvelut"
    ]
  },
  {
    "questionId": 35,
    "questionText": "Opintojesi toteutusmuoto?",
    "questionType": "radioButton",
    "options": [
      "Päivätoteutus",
      "Monimuoto"
    ]
  },
  {
    "questionId": 36,
    "questionText": "Ikäsi:",
    "questionType": "radioButton",
    "options": [
      "alle 18-vuotias",
      "18-24-vuotias",
      "25-29-vuotias",
      "30-34-vuotias",
      "35 tai yli"
    ]
  },
  {
    "questionId": 37,
    "questionText": "Sukupuolesi:",
    "questionType": "radioButton",
    "options": [
      "Mies",
      "Nainen",
      "Muu",
      "En halua kertoa"
    ]
  },
  {
    "questionId": 38,
    "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 39,
    "questionText": "Arviosi opetuksen laadusta:",
    "questionType": "text",
    "options": []
  },
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey or questions not found
- `500 Internal Server Error`

***

# Responses

### Base URL
`https://kysely-spring-git-backend.2.rahtiapp.fi/api/responses`

## Endpoints 

## Save Survey Responses
Saves one or more responses to a specific survey.
Although the backend mainly serves Thymeleaf-rendered pages, this endpoint is intentionally exposed for AJAX or external clients (Bruno/Postman).

**Request:**
- HTTP Method: `POST`
- Endpoint: `/api/surveys/{surveyId}/responses`
- Path Parameters: `{surveyId}` (Long, required): The unique identifier of the survey to which the responses belong.

**Example Request:**
```
POST /api/surveys/6/responses
Content-Type: application/json
[
  {
    "responseText": "Kolmannen vuoden",
    "question": { "questionId": 33 }
  },
  {
    "responseText": "ICT-infra ja pilvipalvelut",
    "question": { "questionId": 34 }
  },
  {
    "responseText": "Monimuoto",
    "question": { "questionId": 35 }
  }, 
  
  (lisää vastauksia)
]
```

**Response:**
- Body: JSON array of objects of the saved responses. Includes generated fields such as `responseId` and full question details.

**Example Response:**
```
[
  {
    "responseId": 140,
    "responseText": "Kolmannen vuoden",
    "question": {
      "questionId": 33,
      "questionText": "Monennenko vuoden opiskelija olet?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 141,
    "responseText": "ICT-infra ja pilvipalvelut",
    "question": {
      "questionId": 34,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "radioButton",
      "options": [
        "ICT ja liiketoiminta",
        "ICT-infra ja pilvipalvelut",
        "Ohjelmistokehitys",
        "Digitaaliset palvelut"
      ]
    }
  },
  {
    "responseId": 142,
    "responseText": "Monimuoto",
    "question": {
      "questionId": 35,
      "questionText": "Opintojesi toteutusmuoto?",
      "questionType": "radioButton",
      "options": [
        "Päivätoteutus",
        "Monimuoto"
      ]
    }
  },
  (lisää vastauksia)
]
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `400 Bad Request` – Invalid request body
- `404 Not Found` – Question not found

***
## Get all Responses by surveyId
Fetch all responses of a specific survey by its unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/api/surveys/{surveyId}/responses`
- Path Parameters: `{surveyId}` (Long, required): The unique identifier of the survey to which the responses belong 

**Example Request:**
`GET /api/surveys/2/responses`

**Response:**
- Body: JSON array of objects with all of the survey's response details.

**Example Response:**
```
  {
    "responseId": 4,
    "responseText": "Toisen vuoden opiskelija",
    "question": {
      "questionId": 4,
      "questionText": "Monennenko vuoden opiskelija olet?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 5,
    "responseText": "Ohjelmistokehitys",
    "question": {
      "questionId": 5,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 6,
    "responseText": "Päivätoteutus",
    "question": {
      "questionId": 6,
      "questionText": "Opintojesi toteutusmuoto?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 7,
    "responseText": "31",
    "question": {
      "questionId": 7,
      "questionText": "Ikäsi:",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 8,
    "responseText": "Nainen",
    "question": {
      "questionId": 8,
      "questionText": "Sukupuolesi:",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 9,
    "responseText": "Tarjontaa on hyvin",
    "question": {
      "questionId": 9,
      "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
      "questionType": "text",
      "options": []
    }
  }
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey, questions or responses not found: `{surveyId}`
- `500 Internal Server Error`

<!-- Below is a template!
***
## Method
description

**Request:**
- HTTP Method: `GET`
- Endpoint: `/`
- Path Parameters: `{}` (type, (required)): The unique identifier of xxx

**Example Request:**
`GET / POST / PUT`

**Response:**
- Body:

**Example Response:**
```
```
***
--!>






