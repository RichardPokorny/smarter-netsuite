# smarter-netsuite
A collection of useful SuiteScripts and tools for NetSuite ERP.

## Useful snippets for Browser Console
### Update subsidiary of a project
```
const newSubsidiary = "14";
const customer = nlapiGetFieldValue('parent');
const oldSubsidiary = nlapiGetFieldValue('subsidiary');


nlapiSubmitField(nlapiGetRecordType(), nlapiGetRecordId(), ['parent', 'subsidiary'], [null, oldSubsidiary]);

nlapiSubmitField(nlapiGetRecordType(), nlapiGetRecordId(), ['parent', 'subsidiary'], [customer, newSubsidiary]);
```

## Useful Formulas in NetSuite Saved Searches
### Show a Customer/Vendor Name in a single column when A/P, A/R, and Journals are present in search results:
Use formula `COALESCE({name}, {vendor.entityid})`

### Link to a transaction using a custom body field
`<a href="https://XXX.app.netsuite.com/app/accounting/transactions/vendbill.nl?id='|||{custbody_YYY}||'"target="_blank">'||{custbody_YYY}||'</a>`
