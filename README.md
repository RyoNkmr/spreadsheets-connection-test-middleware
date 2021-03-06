# spreadsheets-connection-test-middleware
express middleware

## setting

```javascript
// app.js

var express = require('express');
var app = express();

var spreadsheetsConnectionTestMiddleware = require('spreadsheets-connection-test-middleware');

var spreadsheetSettings = {
 // ex.) https://docs.google.com/spreadsheets/d/HOGEHOGEHOGEHOGEHOGE/edit
  sheetId: 'sheetid is HOGEHOGEHOGEHOGEHOGE',
  //and you must get creds for spreadsheets API at https://console.developers.google.com/
  privateKey: '-----BEGIN PRIVATE KEY-----\nYOU_MUST_GET_THIS_KEY_FROM_CONSOLE_DEVELOPERS_GOOGLE_COM_FOR_EXAMPLE_YOU_ADD_A_PROJECT_AND_ENABLE_GOOGLE_DRIVE_API_AND_THEN_GENERATE_SERVICE_ACCOUNT_WITH_KEY_FILE_AS_JSON_THEN_OPEN_THAT_JSON_FILE_CONTAINS_PRIVATE_KEY_LIKE_THIS!!_\n-----END PRIVATE KEY-----\n',
  clientEmail: 'this.is.also.included@in.secrets.json.file'
};

app.use('/spreadsheets', spreadsheetsConnectionTestMiddleware(spreadsheetSettings));
```

## usage
* [POST] ```/spreadsheets/test``` - test connecting and work with sheetAPI.

    1. get information
    1. add a worksheet
    1. change title
    1. set header row
    1. get rows 
    1. resize worksheet
    1. add rows
    1. delete worksheet

```javascript
// no need for Request body nor params

// but response like
{
  addWorksheet: true,
  setTitle: true,
  setHeaderRow: true,
  getRows: true,
  resize: true,
  addRow: true,
  del: true
}
```
