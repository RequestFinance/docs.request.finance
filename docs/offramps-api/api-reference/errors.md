# Errors

Below is a list of errors that can be returned in response to one of your calls.

The response will be formatted as follows:

```json5
{
    error_code: (the error code listed below),
    message: (a description of what went wrong),
    status: (the relevant http status code listed below
}
```

| Error Code                       | Status | Meaning                                                                                                 | Location                       |
| -------------------------------- | ------ | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| unauthorized                     | 401    | Your API key couldn't be read or wasn't valid                                                           | API-wide                       |
| unknown\_format                  | 400    | Your request was not specifying JSON as a response type                                                 | API-wide                       |
| unknown\_http\_method            | 400    | Your request was not specifying a known HTTP method (GET, POST, etc.)                                   | API-wide                       |
| parameter\_missing               | 400    | Your request was missing a required parameter                                                           | API-wide                       |
| bad\_request                     | 422    | Your request was formatted in a way that could not be handled                                           | API-wide                       |
| record\_not\_found               | 404    | A specified record does not seem to exist                                                               | API-wide                       |
| record\_not\_unique              | 422    | A record you are trying to create already seems to exist                                                | API-wide                       |
| record\_invalid                  | 422    | A record you are trying to create or update has some attributes that do not satisfy validation criteria | API-wide                       |
| value\_too\_long                 | 422    | A record you are trying to create or update has some attributes that are too long                       | API-wide                       |
| no\_kyb\_match\_found            | 404    | No KYB record with a matching company number was found                                                  | Users#Sync\_kyb                |
| not\_yet\_passed\_kyc\_kyb       | 422    | User has not yet passed KYC/KYB.                                                                        | PaymentDetails#Create          |
| not\_approved\_for\_payout\_rail | 422    | User is trying to create a PaymentDetail for a currency they have not been approved for.                | PaymentDetails#Create          |
| quote\_already\_executed         | 422    | Quote has already been executed                                                                         | Quotes#Execute                 |
| no\_offramps\_present            | 422    | No Offramps have been created for the Quote                                                             | Quotes#Execute                 |
| sum\_mismatch                    | 422    | The value of the Offramps do not match up with the value of the Quote                                   | Quotes#Execute                 |
| payment\_detail\_not\_approved   | 422    | One or more Payment Details are not cleared for use.                                                    | Quotes#Execute                 |
| currency\_mismatch               | 422    | Destination currency of one or more Offramps is not the same as it's Quote                              | Quotes#Execute                 |
| below\_currency\_limit           | 422    | The specified amount is below the minimum threshold for the requested payout currency                   | Quotes#Create, Offramps#Create |
| invalid\_kyc\_status\_param      | 422    | The status you provided is not supported                                                                | Sandbox::Kyc#Update            |

