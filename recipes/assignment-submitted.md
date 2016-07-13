# VLE User Submits Assignment Recipe
Revision: 1.1

## Purpose
This activity records a user submitting an assignment
## Definition

### Actor
Common entity identifier:  Actor.A


#### Entity Example:
The actor entity describes the individual who has submitted the assignment.


<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
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
Common entity identifier: Verb.A

#### Entity Example:

The Verb, [completed](/vocabulary.md#verbs) describes the action of completing an activity - finishing in its entirety.

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
        "id": "http://adlnet.gov/expapi/verbs/completed",
        "display": {
            "en": "completed"
        }
    },
``` 

### Result.A
Common entity identifier: Result.A

#### Entity Example:
The optional result entity can include completion. See [the xAPI specification for a full description of the result entity](https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md#result)

<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
	<tr>
		<td>result.result.completion</td>
		<td>"true". Indicates the Activity was completed</td>
	</tr>
</table>

``` javascript
 "result":{
        "completion":true
    }
```

### Object
Common entity identifier: Object.B

#### Entity Example:
The object defines the activity that has been completed. [Examples of valid object.definition vocabulary  Activity object Types](/common_statements.md#object) can be found on the vocab page.

<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
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
		<td>JSON object. Object.definition.type identifies the activity.</td>
	</tr>
	</tr>
		<tr>
		<td>object.extension</td>
		<td>JSON object. "http://xapi.jisc.ac.uk/dueDate" is a ISO 8601 date time that the assignment is due</td>
	</tr>
</table>

Example:

``` javascript

"object":{
		"objectType":"Activity",
		"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
		"definition":{
			"type":"http://adlnet.gov/expapi/activities/module",
			"name":{
				"en":"Course Assignment"
			},
			"description":{
				"en":"Course Assignment description"
				}
			},
			
		    "extensions":{
				"http://xapi.jisc.ac.uk/dueDate": "2016-02-05T17:59:45.000Z"
			}
			
		}
		
```


### Context
Common entity identifier: Context.B

#### Entity Example:
Plugin specific extensions are optional and not part of the core recipe.

<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
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
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
                    "definition":{
                        "type":"http://xapi.jisc.ac.uk/courseArea",
                        "name":{
                            "en":"xAPI Basics"
                        },
                        "description":{
                            "en":"xAPI Basics course for Learning Analytics enthusiasts"
                        }
                    }
                }
            ]
        },
        
        "platform": "Moodle",
        "extensions": {
		
      		"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
                "id": http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
            },
			
 			"http://xapi.jisc.ac.uk/sessionId":"32456891",
            "http://id.tincanapi.com/extensions/ip-address": "10.3.3.48"
        }
```




### Complete VLE Specific Examples
[Blackboard Assignment Submitted Example](/vle/blackboard/assignment_submitted.json)

[Moodle Assignment Submitted Example](/vle/moodle/assignment_submitted.json)
