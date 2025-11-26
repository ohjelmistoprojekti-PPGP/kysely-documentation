# Surveys
<!-- Description? -->


### Base URL

`https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys`


## Endpoints

### Get all surveys
Fetch all existing surveys

**Request:**

- HTTP Method: `GET`
- Endpoint: `/surveys`
- Request Parameters: None

**Response:**
JSON object with an `_embedded` field containing an array of surveys. Each survey object includes the following fields:
- `surveyId:` The survey's automatically generated, unique identifier. (long)
- `surveyName:` The survey's name. (string)
- `surveyDesc:` The survey's description. (string)
- `createdDate:`  The survey's date of creation, generated automatically to correspond current date. (localDateTime)
- `startingDate:` Date when the survey starts accepting answers. (string)
- `endingDate:` Date when the survey stops accepting answers. (string)
<!-- A list of questions and answers? -->

**Example Response:**

```
{
    "surveyId": 1,
    "surveyName": "Eläintesti",
    "surveyDesc": "Selvitä mikä eläin olet",
    "createdDate": "2025-11-25T19:13:53.558667",
    "startingDate": "12.12.2025",
    "endingDate": "12.12.2025",
    "questions": [
      {
        "questionId": 1,
        "questionText": "Oletko viekas",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 2,
        "questionText": "Oletko älykäs",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 3,
        "questionText": "Oletko lempeä",
        "questionType": "text",
        "options": []
      }
    ]
  },
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
    "endingDate": "20.1.2.2025",
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
  },
  {
    "surveyId": 4,
    "surveyName": "Testi kysely",
    "surveyDesc": "Tarkoitus on testata onnistuuko kyselyn luonti Rahdin kautta ja hakeeko julkaistu front end sen.",
    "createdDate": "2025-11-25T19:21:50.249925",
    "startingDate": "2025-11-25",
    "endingDate": "2025-11-30",
    "questions": [
      {
        "questionId": 18,
        "questionText": "Miten hyvin tämä toimii?",
        "questionType": "text",
        "options": []
      },
      {
        "questionId": 19,
        "questionText": "Monivalintakysymykset näkyy ne:",
        "questionType": "radioButton",
        "options": [
          "Oikein ",
          "Väärin"
        ]
      }
    ]
  }
```
***
### Get survey by id
Fetch a specific survey by it's unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/surveys/{id}`
- Path Parameters: `{id}` (long, required): The unique identifier of the survey

**Example Request:**
`GET /surveys/2`

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
***
<!-- Tää on mulle ihan kysymysmerkki -->
### Create a new survey
Create a new survey.

**Request:**

- HTTP Method: `POST`
- Endpoint: `/surveys`
- Request Headers:
    - `'Content-Type' : 'application/json'` 
    <!-- ???? -->
- Request Body: JSON object with the following fields (all required)
    - `surveyName:` The survey's name. (string, required)
    - `surveyDesc:` The survey's description. (string)
    - `startingDate:` Date when the survey starts accepting answers. (string, required)
    - `endingDate:` Date when the survey stops accepting answers. (string, required)

**Example Request:**
```
POST https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys
Content-Type: application/json
{
    "surveyName": "Leipätesti",
    "surveyDesc": "Mikä leipä olisit",
    "startingDate": "20.11.2025",
    "endingDate": "30.11.2025"
}
```

**Response:**
- Body: JSON object with the created survey's details.
***
### Update survey
Update a specific survey's details.

**Request:**
- HTTP Method: `PUT`
- Endpoint: `/surveys/{id}`
- Path Parameters: `{id}` (long, required): The unique identifier of the survey
- Request Headers:
    - `'Content-Type' : 'application/json`
- Request body: JSON object containing the updated survey details (all fields optional)

**Example Request:**

```
PUT /surveys/3
Content-Type: application/json

{
    "surveyName": "Leipätesti",
    "surveyDesc": "Mikä leipä olisit",
    "createdDate": "2025-11-19T13:00:20.553279",
    "startingDate": "20.11.2025",
    "endingDate": "30.11.2025"
}
```

**Response:**
- Body: JSON object with the updated survey's details.
***
### Delete survey
Delete a specific survey.

**Request:**
- HTTP Method: `DELETE`
- Endpoint: `/surveys/{id}`
- Path Parameters: `{id}` (long, required): The unique identifier of the survey

**Response:**
<!-- ???????  -->
Upon successful deletion, the API will return a 204 No Content status code. If the customer with the provided id does not exist, the API will return a 404 Not Found status code.

**Important Note:**
Deleting a survey will also delete all associated questions and responses. This operation cannot be undone, so ensure that you want to delete the survey and all it's associated features before making this request.

## Notes:
- **Minttu** (19.11.2025): Work in progress



