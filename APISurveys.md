# Surveys
This backend primarily provides server-rendered Thymeleaf views, but it also exposes a small number of REST endpoints for saving survey responses. These endpoints are intended for use by JavaScript calls or external tools (Bruno/Postman).

**Note:** This backend is not designed as a full REST API. Only the endpoints listed here are intended to be used programmatically.

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
    "surveyId": 2,
    "surveyName": "HH-kysely",
    "surveyDesc": "Kerro, mitä mieltä olet HH IT-Tradenomin koulutusohjelman opetuksen laadusta!",
    "createdDate": "2025-11-25T19:13:54.43315",
    "startingDate": "13.11.2025",
    "endingDate": "22.12.2025",
    "questions": [
      {
        "questionId": 4,
        "questionText": "Monennenko vuoden opiskelija olet?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 5,
        "questionText": "Opintojesi suuntaus?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 6,
        "questionText": "Opintojesi toteutusmuoto?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 7,
        "questionText": "Ikäsi:",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 8,
        "questionText": "Sukupuolesi:",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 9,
        "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 10,
        "questionText": "Arviosi opetuksen laadusta:",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 11,
        "questionText": "Kuinka hyvin koet opintojen valmistavan sinua työelämään?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 12,
        "questionText": "Kuinka hyvin koet kurssien vastaavan kuvauksia?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 13,
        "questionText": "Kuinka todennäköisesti suosittelisit omaa suuntautumistasi muille? (1-5)",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 14,
        "questionText": "Kuinka todennäköisesti suosittelisit HH IT-Tradenomin koulutusohjelmaa muille? (1-5)",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 15,
        "questionText": "Vapaata palautetta/kehitysideoita:",
        "questionType": "text",
        "options": []
      }
    ]
  },
  {
    "surveyId": 3,
    "surveyName": "Elementtikysely",
    "surveyDesc": "1 monivalinta kysymys ja 1 tekstikysymys",
    "createdDate": "2025-11-25T19:13:54.451125",
    "startingDate": "18.11.2025",
    "endingDate": "20.12.2025",
    "questions": [
      {
        "questionId": 16,
        "questionText": "Minkä näistä valitsisit?",
        "questionType": "radioButton",
        "options": [
          "tuli",
          "vesi",
          "ilma",
          "maa"
        ]
      },
      {
        "questionId": 17,
        "questionText": "Miksi valitsit juuri kyseisen elementin?",
        "questionType": "text",
        "options": []
      }
    ]
  }
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
`GET /api/surveys/2`

**Response:**
- Body: JSON object with the survey's details.


**Example Response:**

```
{
  "surveyId": 2,
  "surveyName": "HH-kysely",
  "surveyDesc": "Kerro, mitä mieltä olet HH IT-Tradenomin koulutusohjelman opetuksen laadusta!",
  "createdDate": "2025-11-25T19:13:54.43315",
  "startingDate": "13.11.2025",
  "endingDate": "22.12.2025",
  "questions": [
    {
      "questionId": 4,
      "questionText": "Monennenko vuoden opiskelija olet?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 5,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 6,
      "questionText": "Opintojesi toteutusmuoto?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 7,
      "questionText": "Ikäsi:",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 8,
      "questionText": "Sukupuolesi:",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 9,
      "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 10,
      "questionText": "Arviosi opetuksen laadusta:",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 11,
      "questionText": "Kuinka hyvin koet opintojen valmistavan sinua työelämään?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 12,
      "questionText": "Kuinka hyvin koet kurssien vastaavan kuvauksia?",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 13,
      "questionText": "Kuinka todennäköisesti suosittelisit omaa suuntautumistasi muille? (1-5)",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 14,
      "questionText": "Kuinka todennäköisesti suosittelisit HH IT-Tradenomin koulutusohjelmaa muille? (1-5)",
      "questionType": "text",
      "options": []
    },
    {
      "questionId": 15,
      "questionText": "Vapaata palautetta/kehitysideoita:",
      "questionType": "text",
      "options": []
    }
  ]
}
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey not found: `{surveyId}`
- `500 Internal Server Error`

***

### Get Questions by Survey Id
Fetch a specific survey's questions by its unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/api/surveys/{surveyId}/questions`
- Path Parameters: `{surveyId}` (long, required): The unique identifier of the survey


**Example Request:**
`GET /api/surveys/2/questions`

**Response:**
- Body: JSON array of objects with the survey's question details. No survey details included.

**Example Response:**
```
  {
    "questionId": 4,
    "questionText": "Monennenko vuoden opiskelija olet?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 5,
    "questionText": "Opintojesi suuntaus?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 6,
    "questionText": "Opintojesi toteutusmuoto?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 7,
    "questionText": "Ikäsi:",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 8,
    "questionText": "Sukupuolesi:",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 9,
    "questionText": "Arviosi kurssitarjonnasta suuntautumisessasi:",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 10,
    "questionText": "Arviosi opetuksen laadusta:",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 11,
    "questionText": "Kuinka hyvin koet opintojen valmistavan sinua työelämään?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 12,
    "questionText": "Kuinka hyvin koet kurssien vastaavan kuvauksia?",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 13,
    "questionText": "Kuinka todennäköisesti suosittelisit omaa suuntautumistasi muille? (1-5)",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 14,
    "questionText": "Kuinka todennäköisesti suosittelisit HH IT-Tradenomin koulutusohjelmaa muille? (1-5)",
    "questionType": "text",
    "options": []
  },
  {
    "questionId": 15,
    "questionText": "Vapaata palautetta/kehitysideoita:",
    "questionType": "text",
    "options": []
  }
```

**Possible status codes:**
- `200 OK` – Request succeeded
- `404 Not Found` - Survey or questions not found
- `500 Internal Server Error`

***
## Save Survey Responses
Saves one or more responses to a specific survey.
Although the backend mainly serves Thymeleaf-rendered pages, this endpoint is intentionally exposed for AJAX or external clients (Bruno/Postman).

**Request:**
- HTTP Method: `POST`
- Endpoint: `/api/surveys/{surveyId}/responses`
- Path Parameters: `{surveyId}` (Long, required): The unique identifier of the survey to which the responses belong.

**Example Request:**
```
POST /api/surveys/2/responses
Content-Type: application/json

[
  {
    "responseText": "Sample answer",
    "question": {
      "questionId": 5
    }
  }
]
```

**Response:**
- Body: JSON array of objects of the saved responses. Includes generated fields such as `responseId` and full question details.

**Example Response:**
```
[
  {
    "responseId": 28,
    "responseText": "Testivastaus",
    "question": {
      "questionId": 5,
      "questionText": "Opintojesi suuntaus?",
      "questionType": "text",
      "options": []
    }
  }
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
  },
  {
    "responseId": 10,
    "responseText": "Hyvin paljon opettajakohtaista",
    "question": {
      "questionId": 10,
      "questionText": "Arviosi opetuksen laadusta:",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 11,
    "responseText": "Osa kursseista hyvin, mutta valitettavasti suurin osa ei ollenkaan",
    "question": {
      "questionId": 11,
      "questionText": "Kuinka hyvin koet opintojen valmistavan sinua työelämään?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 12,
    "responseText": "Ei mielestäni joka kerta osu nappiin",
    "question": {
      "questionId": 12,
      "questionText": "Kuinka hyvin koet kurssien vastaavan kuvauksia?",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 13,
    "responseText": "5",
    "question": {
      "questionId": 13,
      "questionText": "Kuinka todennäköisesti suosittelisit omaa suuntautumistasi muille? (1-5)",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 14,
    "responseText": "3",
    "question": {
      "questionId": 14,
      "questionText": "Kuinka todennäköisesti suosittelisit HH IT-Tradenomin koulutusohjelmaa muille? (1-5)",
      "questionType": "text",
      "options": []
    }
  },
  {
    "responseId": 15,
    "responseText": "En osaa sanoa",
    "question": {
      "questionId": 15,
      "questionText": "Vapaata palautetta/kehitysideoita:",
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




