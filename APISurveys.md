# Surveys
Additional information about your API call. Try to use verbs that match both request type (fetching vs modifying) and plurality (one vs multiple).

## Base URL

https://kysely-spring-git-backend.2.rahtiapp.fi/api/surveys

## Endpoints

### Get all surveys
Fetch all existing surveys

Request:

- HTTP Method: `GET`
- Endpoint: `/surveys`
- Request Parameters: None

Response: JSON object with an `_embedded` field containing an array of surveys. Each survey object includes the following fields:
- `surveyId:` The survey's automatically generated, distinctive number. (long)
- `surveyName:` The survey's name. (string)
- `surveyDesc:` The survey's description. (string)
- `createdDate:`  The survey's date of creation, generated automatically to correspond current date. (localDateTime)
- `startingDate:` Date when the survey starts accepting answers. (string)
- `endingDate:` Date when the survey stops accepting answers. (string)
<!-- A list of questions and answers? -->

Example Response:

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


### Get survey by id
Fetch xxx

Request:

- HTTP Method:
- Endpoint:
- Request Parameters:

Response:

Example Response:

### Create a new survey
Fetch xxx

Request:

- HTTP Method:
- Endpoint:
- Request Parameters:

Response:

Example Response:

### Update survey
Fetch xxx

Request:

- HTTP Method:
- Endpoint:
- Request Parameters:

Response:

Example Response:

### Delete survey
Fetch xxx

Request:

- HTTP Method:
- Endpoint:
- Request Parameters:

Response:

Example Response:

## Notes:


<This is where all uncertainties, commentary, discussion etc. can go. I recommend timestamping and identifying oneself when leaving comments here.>
