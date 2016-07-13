# VLE User Logged In Recipe
Revision: 1.1

## Purpose
This activity records a user logging in to a VLE.
## Definition

### Actor
Common entity identifier:  Actor.A

The entity is used across all recipes in the Jisc profile.

#### Entity Example:
The actor entity describes the individual that is logging in to the system.

<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
	<tr>
		<td>actor.objectType</td>
		<td>"Agent"</td>
	</tr>
	<tr>
		<td>actor.name</td>
		<td>Full name of user, optional.</td>
	</tr>

		<tr>
		<td>actor.account</td>
		<td>JSON Object with unique id(account.name) and home page(account.homepage)</td>
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
Common entity identifier: Verb.A

The entity is used across all recipes in the Jisc profile.

#### Entity Example:
The Verb, [logged in](/vocabulary.md#verbs) describes the action of logging into a platform.


<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
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
        "id": "https://brindlewaye.com/xAPITerms/verbs/loggedin/",
        "display": {
            "en" : "logged in to"
        }
    },
``` 
### Context
Common entity identifier: Context.A

#### Entity Example:
Contextual information. Plugin specific extensions are optional and not part of the core recipe.

<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
	<tr>
		<td>context.platform</td>
		<td>The platform used in the experience of this learning activity.</td>
	</tr>
	<tr>
		<td>context.extensions</td>
		<td>The sessionID extension is the VLE session ID. <a href="https://registry.tincanapi.com/#uri/extension/310">IP Address</a> is used to identify the client's real address as a Context extension.</td>
	</tr>
</table>



``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
 			"http://xapi.jisc.ac.uk/sessionId": "32456891",
        		 "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48"
        }
```



### Object

Common entity identifier: Object.A

#### Entity Example:

The object.definition.name and object.definition.definition describe the resource returned to the user after they have performed the logged in event. The object.definition.extensions.[subType](http://xapi.jisc.ac.uk/subType) is used to identify the system type that is being logged into, in this example a lms, identified by  http://id.tincanapi.com/activitytype/lms

<table>
	<tr><th>Property</th><th>Description</th></tr>
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
		<td>A JSON object. object.definition.type describes the activity. object.definition.extensions.subtype can be used to described the subtype of this activity.</td>
	</tr>
</table>

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
        },
```

### Complete VLE Specific Examples
[Moodle Login Example](/vle/moodle/login.js)

[Blackboard Login Example](/vle/blackboard/loggedin.json)
