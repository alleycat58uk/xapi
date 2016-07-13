# VLE User Logged Out Recipe
Revision: 1.1

## Purpose
This activity records a user logging out of a VLE.
## Definition
### Actor
Common entity identifier:  Actor.A

This common statement is used across all example recipes.

#### Entity Example:
The actor entity describes the individual logging out of the system.

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

This common statement is used across all example recipes

#### Entity Example:
The Verb,[logged out](/vocabulary.md#verbs) describes the action of logging out of a platform.

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
        "id": "https://brindlewaye.com/xAPITerms/verbs/loggedout",
        "display": {
            "en": "logged out of"
        }
    },
``` 
### Context
Common entity identifier: Context.A

#### Entity Example:
[Context](/common_statements.md#context) identifies the platform that is being logged out of, Moodle in this example. Plugin specific extensions are optional and not part of the core recipe.

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
 			"http://xapi.jisc.ac.uk/sessionId":"32456891",
        		  "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48"    
        }
```

### Object
Common entity identifier: Object.A

#### Entity Example:

The object.definition.name and object.definition.definition describe the resource logged out of. The object.definition.extensions.[subType](http://xapi.jisc.ac.uk/subType) is used to identify the system type that is being logged into, in this example a lms, identified by  http://id.tincanapi.com/activitytype/lms

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
		<td>A JSON object. Object.definition.type describes the activity and object.definition.extensions.subtype can be used to described the subtype of this activity.</td>
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

Moodle (ToDo)

[Blackboard](blackboard/loggedout.json)
