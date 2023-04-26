# smarter-netsuite
A collection of useful SuiteScripts and tools for NetSuite ERP.

## Useful snippets for Browser Console

### Update external ID of a record based on another field on the record
This snippet sets external ID based on another field that is specifed in SOURCE_FIELD variable. This code has to be run on the record whose external ID is to be updated.

```
const SOURCE_FIELD = 'name' // Replace with script ID of a field that has value that will be set as external ID

require(['N/currentRecord', 'N/record'], function(currentRecord, record) {
    const recordToUpdate = currentRecord.get()
    const externalIdValue = recordToUpdate.getValue({fieldId: SOURCE_FIELD})
    
    console.warn('Record Internal ID: ' + recordToUpdate.id + ' | Record Type: ' + recordToUpdate.type + ' | External ID value to be set: ' + externalIdValue)
    
    record.submitFields({type: recordToUpdate.type, id: recordToUpdate.id, values: {'externalid': externalIdValue}})
})
```

### Update subsidiary of a project
This snippet is useful when a project has assigned a correct customer, but incorrect subsididary of that customer. Just replace XXX with internal ID for the right subsidiary and run the code in Console.
```
const newSubsidiary = XXX; //Replace with internal ID of new subsidiary of the project
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
