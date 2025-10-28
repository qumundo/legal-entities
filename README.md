# Legal entities
Access the global Legal Entity Identifier (LEI) database with multi-tag filter options on appropriate parameters. The LEI (Legal Entity Identifier) is a unique 20 digit alphanumeric code based on ISO 17442 standard assigned to legal entities and enables clear and unique identification of legal entities participating in transactions globally, including financial services, supply chain, trade finance and payments. Numerous regulatory requirements around the globe either require, request or recommend the usage of LEIs. Available data and information include LEI-identifier, LEI-reference data (Who is who?), LEI-relationship data (Who owns whom?), LEI-mapping data (LEI-ISIN, LEI-BIC or LEI-MIC) and LEI-meta data (authorities, legal forms, organizational roles, jurisdictions).

Documentation, Examples, FAQ, Terms & Conditions and License: [https://www.qumundo.com/docs/legal-entities-lei-data](https://www.qumundo.com/docs/legal-entities-lei-data).

If you see a feature that is missing or not correctly enforced, please [open an issue](https://github.com/qumundo/legal-entities/issues).

_You can find example filter parameter (key) and response schema in the JSON file here: [example.json](https://github.com/qumundo/legal-entities/blob/master/res/example.json)_

**:de: Crafted in Frankfurt am Main, Germany.**

## Last changes

Last changes and the version history can be found in the [CHANGELOG.md](https://github.com/qumundo/legal-entities/blob/master/CHANGELOG.md) file.

_As this library is SemVer-compatible, any breaking change would be released as a MAJOR version only. Non-breaking changes and features are released as MINOR. Feature updates and bug fixes are released as PATCH (note that feature updates may as well be bundled under a MINOR release, if it comes with new settings or minor changes)._

## How to install?

Include `legal-entities` in your `package.json` dependencies:

```bash
npm install --save @qumundo/legal-entities
```

## How to use?

This module may be used to access, retrieve and use data and information on legal entities (lei), including its reference data, relationship data, mapping and meta data. You may use multi-tag filter parameters (keys) to build customized queries to your needs.

### :link: Import the module

Import the module in your code:

`const LegalEntities = require("@qumundo/legal-entities")`

### :arrow_right: Get level-1 legal entity reference data (Who is who?)

```javascript

let data = await LegalEntities.getData({ path: "lei/search?" });

/*
data.data[0] ===

{
  "id": 676202,
  "lei": "5299000W0HB7SX4P4882",
  "legal_name": "Mercedes-Benz AG",
  "legal_name_lang": "de-DE",
  "legal_address": "Mercedesstraße 120",
  "legal_address_number": "",
  "legal_address_number_in_building": "",
  "legal_address_mail_routing": "",
  "legal_address_line_1": "",
  "legal_address_line_2": "",
  "legal_address_line_3": "",
  "legal_address_city": "Stuttgart",
  "legal_address_region": "DE-BW",
  "legal_address_country": "DE",
  "legal_address_postal": "70372",
  "legal_address_lang": "de-DE",
  "hq_address": "Mercedesstraße 120",
  "hq_address_number": "",
  "hq_address_number_in_building": "",
  "hq_address_mail_routing": "",
  "hq_address_line_1": "",
  "hq_address_line_2": "",
  "hq_address_line_3": "",
  "hq_address_city": "Stuttgart",
  "hq_address_region": "DE-BW",
  "hq_address_country": "DE",
  "hq_address_postal": "70372",
  "hq_address_lang": "de-DE",
  "registration_authority_id": "RA000351",
  "other_registration_authority_id": "",
  "registration_authority_entity_id": "HRB 762873",
  "legal_jurisdiction": "DE",
  "entity_category": "GENERAL",
  "entity_subcategory": "",
  "entity_legal_form_code": "6QQB",
  "other_legal_form": "",
  "entity_status": "ACTIVE",
  "entity_creation_date": "2017-11-16T23:00:00.000Z",
  "initial_registration_date": "2018-09-27T09:18:19.000Z",
  "last_updated_date": "2024-08-21T10:08:04.000Z",
  "registration_status": "ISSUED",
  "next_renewal_date": "2025-09-27T09:18:19.000Z",
  "managing_lou": "5299000J2N45DDNE4Y28",
  "validation_sources": "FULLY_CORROBORATED",
  "validation_authority_id": "RA000351",
  "other_validation_authority_id": "",
  "validation_authority_entity_id": "HRB 762873"
}

*/
```

### :arrow_right: Get level-2 legal entity relationship data (Who owns whom?)

```javascript

let data = await LegalEntities.getData({ path: "lei/rr/search?" });

/*
data.data[0] ===

{
  "id": 1,
  "start_node": "029200396H3K1YG7D555",
  "start_node_type": "LEI",
  "end_node": "029200388A7S7Z5I0H57",
  "end_node_type": "LEI",
  "relationship_type": "IS_DIRECTLY_CONSOLIDATED_BY",
  "relationship_status": "ACTIVE",
  "initial_registration_date": "2014-11-05T23:00:00.000Z",
  "last_update_date": "2024-11-05T11:34:07.000Z",
  "registration_status": "PUBLISHED",
  "next_renewal_date": "2025-11-05T15:00:00.000Z",
  "managing_lou": "029200067A7K6CH0H586",
  "validation_sources": "FULLY_CORROBORATED",
  "validation_documents": "SUPPORTING_DOCUMENTS",
  "validation_reference": "www.stanbicibtc.com"
}

*/
```

### :arrow_right: Get legal entity meta data

```javascript

let data = await LegalEntities.getData({ path: "lei/meta/search?" });

/*
data.data[0] ===

{
  "id": 343,
  "reg_authority_code": "RA000205",
  "country": "Germany",
  "country_code": "DE",
  "jurisdiction": "Aschaffenburg",
  "reg_name_int": "Commercial Register",
  "reg_name_local": "Handelsregister",
  "reg_org_name_int": "Local Court Aschaffenburg",
  "reg_org_name_local": "Amtsgericht Aschaffenburg",
  "www": "www.handelsregister.de",
  "comments": ""
}

*/
```

### :arrow_right: Get legal entity mapping data

```javascript

let data = await LegalEntities.getData({ path: "lei/mapping/search?" });

/*
data.data[0] ===

{
  "id": 1,
  "lei": "001GPB6A9XPE8XJICC14",
  "isin": "US3158052262"
}

*/
```

### :arrow_right: Get overview of all databases (paths) available

```javascript

let example = await LegalEntities.getExample();

/*
Object.keys(example) ===

[
  'lei/search?',
  'lei/search?db=entityName',
  'lei/search?db=entityNameLang',
  'lei/search?db=successor',
  'lei/search?db=events',
  'lei/search?db=affectedFields',
  'lei/rr/search?',
  'lei/rr/search?db=period',
  'lei/rr/search?db=qualifier',
  'lei/rr/search?db=quantifier',
  'lei/rr/search?db=repex',
  'lei/meta/search?db=authorities',
  'lei/meta/search?db=elf',
  'lei/meta/search?db=oor',
  'lei/meta/search?db=jurisdiction',
  'lei/mapping/search?db=isin',
  'lei/mapping/search?db=bic',
  'lei/mapping/search?db=mic'
]
*/
```

## Filtering

Filtering and customized requests can be built and accomplished by passing filter parameters (objects) to the .getData() instance like:

```javascript
let items = [
  { key: 'lei', value: '529900R27DL06UVNT076' }
];

let data = await LegalEntities.getData({ path: "lei/search?", items });
```

The default filter syntax is LIKE: `=`.

### :arrow_right: Filtering for an exact value (MATCH) attach and change the syntax (filter) like:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes', filter: '==' }
];
```

### :arrow_right: If the search result should not contain a certain value, use a single equal and an exclamation =! sign:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes', filter: '=!' }
];
```

### :arrow_right: When filtering for multiple values of a parameter, use comma separation:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes,Benz' }
];
```

### :arrow_right: To change the operator (default is 'OR') when searching for multiple values of a parameter, attach and change the parameter 'operator' of an object:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes,Benz', operator: 'and' }
];
```

### :arrow_right: When filtering for multiple parameter add another object key:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes' },
  { key: 'legalCity', value: 'Stuttgart' }
];
```

### :arrow_right: To change the operator (default is 'AND') when searching for multiple parameters, attach and change parameter operator in the .getData() instance like:

```javascript
let items = [
  { key: 'legalName', value: 'Mercedes' },
  { key: 'legalCity', value: 'Stuttgart' }
];

let data = await LegalEntities.getData({ path: "lei/search?", items, operator: 'or' });
```

Documentation and examples of available filter options can be found here: [https://www.qumundo.com/docs/introduction#filtering](https://www.qumundo.com/docs/introduction#filtering).

## Pagination

In many occasions too much information is returned in a single request. By default a maximum of 100 records per request will be returned. To receive more records per request, you may specify a `pageSize` (max. 250) parameter object. The response can then be paginated adding and using the `pageNum` parameter:

```javascript
let items = [
  { key: 'pageSize', value: '50' },
  { key: 'pageNum', value: '2' }
];

let data = await LegalEntities.getData({ path: "lei/search?", items });
```

### :arrow_right: Get an overview of all filter parameter (key) for a specific database (path) available call the .getExample() instance with the path:

```javascript

let example = await LegalEntities.getExample({ path: "lei/search?" });

/*
[
  { key: 'lei', field: 'lei', type: 'string' },
  { key: 'legalName', field: 'legal_name', type: 'string' },
  { key: 'entityStatus', field: 'entity_status', type: 'string' },
  { key: 'legalCountry', field: 'legal_address_country', type: 'string' },
  { key: 'legalCity', field: 'legal_address_city', type: 'string' },
  { key: 'legalJurisdiction', field: 'legal_jurisdiction', type: 'string' },
  { key: 'entityCategory', field: 'entity_category', type: 'string' },
  { key: 'entitySubcategory', field: 'entity_subcategory', type: 'string' },
  { key: 'legalFormCode', field: 'entity_legal_form_code', type: 'string' },
  { key: 'legalForm', field: 'other_legal_form', type: 'string' },
  { key: 'minCreation', field: 'entity_creation_date', type: 'date' },
  { key: 'maxCreation', field: 'entity_creation_date', type: 'date' },
  { key: 'minInitial', field: 'initial_registration_date', type: 'date' },
  { key: 'maxInitial', field: 'initial_registration_date', type: 'date' },
  { key: 'minUpdated', field: 'last_updated_date', type: 'date' },
  { key: 'maxUpdated', field: 'last_updated_date', type: 'date' },
  { key: 'minRenewal', field: 'next_renewal_date', type: 'date' },
  { key: 'maxRenewal', field: 'next_renewal_date', type: 'date' },
  { key: 'registrationStatus', field: 'registration_status', type: 'string' },
  { key: 'lou', field: 'managing_lou', type: 'string' }
]
*/
```

### :arrow_right: Get an example response for a specific database (path) available:

```javascript

let example = await LegalEntities.getExample(false, { path: "lei/search?db=entityName" });

/*
{
  status: 200,
  success: true,
  record_count: 100,
  total_records: 406090,
  page_number: 1,
  page_size: 100,
  total_pages: 4061,
  more_pages: true,
  data: [
    {
      id: 1,
      lei: '029200711C4S4CB2E982',
      entity_name: 'SEPLAT PETROLEUM DEVELOPMENT COMPANY PLC',
      lang: 'en',
      type: 'TRADING_OR_OPERATING_NAME'
    },
    {
      id: 2,
      lei: '0292003540H0S4VA7A50',
      entity_name: 'FBNQUEST ASSET MANAGEMENT LIMITED',
      lang: 'en',
      type: 'TRADING_OR_OPERATING_NAME'
    },
    {}
  ]
}
*/
```

## Need more legal entity data?

Choose between various subscription options for your use case: [https://www.qumundo.com/api/legal-entities-lei-data](https://www.qumundo.com/api/legal-entities-lei-data).

Once subscribed and enabled, login to our platform and provide authentication along your request.

### :arrow_right: Login to our platform to receive an authentication token

```javascript
let credentials = { email: config.YOUR_EMAIL, password: config.YOUR_PASSWORD };   // Keep your login credentials secure and secret

let login = await LegalEntities.getLogin(credentials);

let token = login.token;
```

### :arrow_right: Get data with your subscription

```javascript
let data = await LegalEntities.getData({ path: "lei/search?" }, token);
```

_If you need additional features, changes or notice any discrepancies, feel free to submit a Pull Request._

**Consider supporting the development by [making a donation](https://github.com/sponsors/qumundo).**
