# VLE Session timed out recipe
Revision: 1.1

## Purpose
This activity indicates the activity provider has determined that the session was abnormally terminated either by an actor or due to a system failure.

This recipe may not work reliably across VLEs.
## Definition
### Actor

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

The Verb,[abandoned](/vocabulary.md#verbs) describes the action of logging out of a platform.

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

Example:

``` javascript
"verb": {
        "id": "https://w3id.org/xapi/adl/verbs/abandoned",
        "display": {
            "en": "session timed out"
        }
    },
``` 

### Context
Context identifies the platform that is being logged into, Moodle in this example. Plugin specific extensions are optional and not part of the core recipe.

<table>
	<tr><th>Property</th><th>Jisc Profile Information</th></tr>
	<tr>
		<td>context.platform</td>
		<td>The platform used in the experience of this learning activity.</td>
	</tr>
	<tr>
		<td>context.platform.extensions</td>
		<td>The sessionID extension is the VLE session ID. [IP Address](https://registry.tincanapi.com/#uri/extension/310) is used to identify the client's real address as a Context extension.</td>
	</tr>
	<tr>
		<td>context.context.activities</td>
		<td>Has a context type of grouping. A course that relates to a assignment as the parent.</td>
	</tr>
</table>

Example:

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
 		"http://xapi.jisc.ac.uk/sessionId": "32456891",
		"http://id.tincanapi.com/extensions/ip-address" :"10.3.3.48"
              
        }
```

### Object


The object defines the item that the user has timed out of.  A [Jisc specific extension](common_statements.md#jisc_extensions) details that it is a VLE that is being logged out of. 
``` javascript

"object": {
    "objectType": "Activity",
    "id": "https://courses.alpha.jisc.ac.uk/moodle",
    "definition": {
        "type": "http://activitystrea.ms/schema/1.0/application",
        "name": {
            "en": "A Moodle course"
        },
        "description": {
            "en": "A Moodle course"
        },
        "extensions": {
            "http://xapi.jisc.ac.uk/subType": "http://id.tincanapi.com/activitytype/lms"
        }
    }
}
```


### Complete VLE Specific Examples
Moodle (ToDo)

[Blackboard](blackboard/loggedout.json)
