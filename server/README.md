# Server Side Code #

Technology Used: Express, Express-session, Mongoose, Twinword API, Google Maps Geocoding API

The file structure of this folder is as follows:

```
├── README.md
├── lib
│   ├── api_config.js
│   ├── billAssociate.js
│   ├── emailWorker.js
│   ├── insertSampleUsers.js
│   ├── request-handler.js
│   ├── sampleUserData.json
│   └── utility.js
├── server-config.js
└── server.js
```

server.js: It includes specification for the http server port as well as db server port.

server-config.js: This file is required by server.js. It includes specifications for the REST API endpoints.

request-handler.js: This file is required by server-config.js. It includes handler functions used by server for:

  Creating user profile and managing client authentication with user database
  -userLogin
  -userLogout
  -userSignup

  Managing app requests with user database
  -insertWordMonitor
  -deleteWordMonitor

  Managing app request with api calls to Twinword API
  -termSearch

utility.js: This file is required by server-config.js and request-handler.js. It includes helper functions used by server for:
  
  Check user authentation
    -isLoggedIn
    -checkUser
    -comparePassword

  Create user session
    -sendUserData
    -createSession

  Managing word monitor with api calls to Twinword API
    -keywordBuilder

  Geocoding user address into longitude and latitude with api calls to Google Maps Geocode service
    -geoCodeIt

emailWorker.js: uses the node-module, nodemailer, to send emails to all users in the users database. Logs the most recent introduced_on date in the emailTimestamp.txt using file system module

If you would like to test the code on your local machine, you can use the insertSampleUsers.js file to insert the sampleUserData.json. NOTE: in the sampleUserData.json, make sure you insert real emails in the data (right now example1@gmail.com is in the fields). 

billAssociate.js: the input of the main export function, billAssociate, is a specific keyword object (example, {keyword: 'immigration'}). Helper functions getAllByKeywords and getAllByKeywordsGen searches through the keywords stored in our bills database and uses a regex to find matches between the user keyword and the keywords/keywords_generated field. The output of billAssociate will be the keyword object with a new field, 'relatedBills', with an array of bill ids related to that keyword. 

api_config.js: This file contains API configurations

