#Reading List View
Revision: 0.1

DRAFT
This is a draft recipe

##Purpose
This recipe defines the structure and terms to record the experience of viewing a reading list

### Actor
Common Statement Identifier:  Actor.A

#### Entity Example:
[Accounts](/common_statements.md#actor.account) is used as the identifer.  Account/Name to use is up to the sender, as long as it is resolvable, unique and persistant.

ToDo: Where does this information come from?

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
		<td>JSON Object with unique id and home page</td>
	</tr>
</table>

``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb
Common Statement Identifier: Verb.A

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

[Context](/common_statements.md#context)
[IP Address](https://registry.tincanapi.com/#uri/extension/310)

``` javascript
"context": {
        "platform": "",
        "extensions": {
 	    "http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
            "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48"
        }
```

### Object
Common Statement Identifier: Object.D

#### Entity Example:
Needs to which reading list was viewed
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
	"id": "http://moodle.data.alpha.jisc.ac.uk/mod/quiz/view.php?id=13"   	 	//  unique id or url of the item being logged into
	"definition": {
		"type": "http://xapi.jisc.ac.uk/define/vle/page",			//  definition type as above
		"name": { "en": "Sample page" },			   //  name of item as returned by VLE
		"description": { "en": "sample page" } //  description of item as returned by VLE
	 }
}
```

### Complete VLE Specific Examples
[Moodle Example](/vle/moodle/moduleview.js)

[Blackboard Example](/vle/blackboard/course_content_access.json)
