# **User Client Authorizations**
---
**API Description:**
Search Client Authorizations of a given logged in BMT/IVR user.


**URI Patterns:**
  /api/v1/client-authorizations?user-id='njodh'


**HTTP Method:**
GET  

**HTTP Headers:**

id_token

client_id

nonce


**OIDC Token Metadata**

user_id

**Security Considerations**

    PII Data: N/A

**API Invocation Patterns:**

**Sample Request:**

  N/A

**Sample Response:**

  ```json
   {
	  "totalCount" : 100,
	  "clientAuthorizations" :
	   [
		{
                "planAcronym" : "DDMN",				
                "application" : "BMTDental",
                "clientSpecifiedId" : "1610",								
                "clientName" : "Singular Individual Plan - AAA",
                "_links": [
        {"self": "/client-authorizations?offset=30&limit=30"},
        {"first": "/client-authorizations?offset=0&limit=30"},
        {"previous": "/client-authorizations?offset=0&limit=30"},
        {"next": "/client-authorizations?offset=60&limit=30"},
        {"last": "/client-authorizations?offset=90&limit=30"},
        {"subclientAuthorizations": "/subclient-authorizations?user-id='njodh'&client-specified-id='1610'&plan-acronym='DDMN'&'application' : 'BMTDental'"
}

      ]
		}
	  ]
	}
  ```

**HTTP Error Handling:**

  * 404 NOT FOUND

```json
{
    "timeStamp":  "11/18/2017 06:49:25",
    "traceId":  "841ad787531ec7e3",
    "apiErrorList":  [{
      "rejectedFieldName":  null,
        "rejectedValue":  null,
        "errorMessage":  "Resource not found!"
      }
    ]
}
  ```

  * 401 UNAUTHORIZED
```json
{
    "timeStamp":  "11/18/2017 06:49:25",
    "traceId":  "841ad787531ec7e3",
    "apiErrorList":  [{
        "rejectedFieldName":  null,
        "rejectedValue":  null,
        "errorMessage":  "Unauthorized!"
      }
    ]
}

  ```

  * 400 BAD REQUEST
```json
{
    "timeStamp":  "11/18/2017 06:49:25",
    "traceId":  "841ad787531ec7e3",
    "apiErrorList":  [{
        "rejectedFieldName":  user-id,
        "rejectedValue":  null,
        "errorMessage":  "user-id is not specified and is required!"
      }
    ]
}

  ```

  * 403 FORBIDDEN
```json
{
    "timeStamp":  "11/18/2017 06:49:25",
    "traceId":  "841ad787531ec7e3",
    "apiErrorList":  [{
        "rejectedFieldName":  null,
        "rejectedValue":  null,
        "errorMessage":  "Forbidden!"
      }
    ]
}

  ```

  * 500 INTERNAL SERVER ERROR
```json
{
    "timeStamp":  "11/18/2017 06:49:25",
    "traceId":  "841ad787531ec7e3",
    "apiErrorList":  [{
        "rejectedFieldName":  null,
        "rejectedValue":  null,
        "errorMessage":  "Internal Server Error!"
      }
    ]
}

  ```


**API Consumer:**
BMT / IVR

**Paging:**

offset

limit

default page size `30`

maximum  `100`

**API Roles and Permissions:**

BMTDental_User

BMTDental_Admin

BMTDental_Supervisor

**API Usage:**

    User is authenticated and has a token before accessing an API

	User can access only his/her data and user_id of id_token should be same as URI's user-id

	Admin / Delegate can access authorizations of all his / her users

**Request:**

1. Name:  **user-id**

    Description: User Identifier of a logged in user.

    Nullable: No.  user-id must be supplied.

    DataType: String



**Response:**

1. Name: **planAcronym**

    Description: Plan Acronym.

    Nullable: No.

    DataType: String

1. Name: **application**

    Description: Application which user has access to.

    Nullable: No.

    DataType: String

1. Name: **clientSpecifiedId**

    Description:   The user-known id of the Client.

    Nullable: No.

    DataType: String

1. Name: **clientName**

    Description:   Client Name

    Nullable: No.

    DataType: String

1. Name: **subClients**

    Description:   HATEOAS link to fetch Sub Client Authorizations of a selected Client.

    Nullable: No.

    DataType: N/A

**API by Architectural Component Type:** 
Data Service, API Gateway

**Existing similar ETS API's:**
N/A

**Existing similar Roosevelt API's:**
N/A