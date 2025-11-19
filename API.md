## General

This REST API is designed to manage the relationship between surveys and it's questions and responses. It provides a set of CRUD (Create, Read, Update, Delete) operations in order to manage surveys and it's associated questions and answers.


## User Instructions

This is BAse API documentation, which means more detailed API documentation is portrayed in each API's documentation file. You can browse different files by clicking the links in the following overview or by using these URL's:

**Surveys:**
https://github.com/ohjelmistoprojekti-PPGP/kysely-documentation/blob/fe9d454bdf17cbb1bc2ff132d0f0abf754a10554/APISurveys.md

**Questions:**
<!-- TO-DO: API-doc linkki -->

**Responses:**
<!-- TO-DO: API-doc linkki -->


## Overview
<!-- TO-DO: linkit API-dokumentaatioihin -->
The API is structured around three main resources: Surveys, Questions and Responses. 
- [Surveys](APISurveys.md) present information of the survey and a list of questions that can be answered. Each survey also has attributes such as name, description, date of creation and starting date and ending date for responding.
- Questions represent interactive fields for surveys. Each question has attributes like the question's type (either  text field or multiple choice via radio button), and the question's heading.
- Responses present a list of responses to a survey or a specific question. Each response has an attribute of response's text or choice in addition of the question it's associated with.

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

## Notes:
- **Minttu** (19.11.2025): Work in progress



