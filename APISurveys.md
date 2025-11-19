# Surveys
<!-- Description? -->

## Base URL

https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys

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
    "createdDate": "2025-11-13T09:47:14.563923",
    "startingDate": "12.12.2025",
    "endingDate": "12.12.2025"
  },
  {
    "surveyId": 2,
    "surveyName": "HH-kysely",
    "surveyDesc": "Kerro, mitä mieltä olet HH IT-Tradenomin koulutusohjelman opetuksen laadusta!",
    "createdDate": "2025-11-13T09:47:15.573179",
    "startingDate": "13.11.2025",
    "endingDate": "22.12.2025"
  }
```

### Get survey by id
Fetch a specific survey by it's unique identifier

**Request:**
- HTTP Method: `GET`
- Endpoint: `/surveys/{id}`
- Path Parameters: {id} (long, required) is the unique identifier of the survey

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
  "createdDate": "2025-11-13T09:47:15.573179",
  "startingDate": "13.11.2025",
  "endingDate": "22.12.2025"
}
```


<!-- Tää on mulle ihan kysymysmerkki -->
### Create a new survey
Create a new survey

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
- Body: JSON object with the created survey's details


### Update survey
Fetch xxx

**Request:**
- HTTP Method:
- Endpoint:
- Request Parameters:

**Response:**

**Example Response:**

```

```


### Delete survey
Fetch xxx

**Request:**
- HTTP Method:
- Endpoint:
- Request Parameters:

**Response:**

**Example Response:**

```

```


## Notes:
- Minttu (19.11.2025): Work in progress
