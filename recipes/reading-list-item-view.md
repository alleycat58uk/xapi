#Reading List View
Revision: 0.1

DRAFT

##Purpose
This recipe defines the structure and terms to record the experience of viewing a reading list

### Actor


#### Entity Example:
The actor entity describes the individual that is viewing  a reading list item.

_ToDo: Where does this information come from?_

<table>
	<tr><th>Property</th><th>Jisc Profile Information</th></tr>
	<tr>
		<td>actor.account</td>
		<td>Full name of user, optional.</td>
	</tr>
	<tr>
		<td>actor.objectType</td>
		<td>Agent</td>
	</tr>
		<tr>
		<td>actor.account</td>
		<td>JSON Object with unique id</td>
	</tr>
</table>

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": " " _// ToDo Check Where we get ID from_
           
        }
    },
```

### Verb


#### Entity Example:

The Verb,[viewed](/vocabulary.md#verbs) denotes the action of the user's browser or app requesting the resource that the user wishes to view.

<table>
	<tr><th>Property</th><th>Jisc Profile Information</th></tr>
	<tr>
		<td>verb.id</td>
		<td>IRI corresponding to Verb.</td>
	</tr>
	<tr>
		<td>verb.display</td>
		<td>Human readable representation of Verb. Key is a RFC 5646 Language Tag</td>
	</tr>
</table>

``` javascript
"verb": {
        "id": "http://id.tincanapi.com/verb/viewed",
        "display": {
            "en": "viewed"
        }
    },
```
### Context


#### Entity Example:
Contexual Information

_ToDo: Check what contexual information the reading list suppliers give us_

``` javascript
"context": {
        "platform": "", // Is this the reading list platform?
        "extensions": {
            "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48" _// ToDo: Check what contexual information we get_
        }
```

### Object


#### Entity Example:
The reading list item that was viewed
_ need to check what is possible here_ 

<table>
	<tr><th>Property</th><th>Jisc Profile Information</th></tr>
	<tr>
		<td>object.objectType</td>
		<td>Must be "Activity".</td>
	</tr>
	<tr>
		<td>object.id</td>
		<td>An identifier for a single unique Activity</td>
	</tr>
		<tr>
		<td>object.definition</td>
		<td>A JSON object. object.definition.type describes the activity and object.definition.extensions.subtype can be used to described the subtype of this activity.</td>
	</tr>
</table>

``` javascript
"object": {
	"objectType": "Activity",
	"id": " "   	 	//  _unique id or url reading list?_
	"definition": {
		"type": "  ",			//  definition type as above _need minting?_
		"name": { "en": "Sample page" },			   //  name of 
		"description": { "en": "sample page" } //  description 
	 }
}
```
