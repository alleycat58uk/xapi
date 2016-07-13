#Module/Block/Object View
Revision: 1.1

##Purpose
This recipe defines the structure and terms to record the experience of viewing a vle resource such as a Moodle Module or Blackboard building block (eg a page as identified by its url)

### Actor
Common entity identifier:  Actor.A

#### Entity Example:
[Accounts](/common_statements.md#actor.account) is used as the identifer.  Account/Name to use is up to the sender, as long as it is resolvable, unique and persistant. Candidates include: vle id, the login name, and an other field with a student id in.

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
Common entity identifier: Verb.A

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
Common entity identifier: Context.C

#### Entity Example:
Plugin specific extensions are optional and not part of the core recipe


<table>
	<tr><th>Property</th><th>Jisc Profile Information</th></tr>
	<tr>
		<td>context.platform</td>
		<td>The platform used in the experience of this learning activity.</td>
	</tr>
	<tr>
		<td>context.extensions</td>
		<td>Json object with the following proerties: The sessionID extension is the VLE session ID. [IP Address](https://registry.tincanapi.com/#uri/extension/310) is used to identify the client's real address as a Context extension. SessionId is the VLE session Id. CourseArea is the umbrella course/parent area identified by its home page URI 
	</td>
	</tr>
</table>

``` javascript
"context": {
        "platform": "Moodle",
        "extensions": {
      			"http://xapi.jisc.ac.uk/courseArea": {
      		 	"http://xapi.jisc.ac.uk/vle_mod_id": "LA101",
                 	"id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4"
		  	"http://xapi.jisc.ac.uk/sessionId": "32456891"  ,
		  	"http://id.tincanapi.com/extensions/ip-address": "10.3.3.48"
			 }
              
        }
```

### Object
Common entity identifier: Object.D

#### Entity Example:
Needs to identify what was viewed. A list of valid values can be found at [the definition of  object.definition.extensions on the vocabulary page](../vocabulary.md#Object.definition.extension)

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
