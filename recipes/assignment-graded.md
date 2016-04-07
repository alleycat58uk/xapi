# VLE Assignment Graded Recipe
Revision: 1.0

## Purpose
This activity records a graded assignment
## Definition
### Actor

[Account](/common_statements.md#actor.account) is used as the identifer.  Account/Name to use is up to the sender, as long as it is resolvable, unique and persistant . Candidates include: vle id, the login name, and an other field with a student id in.


``` Javascript
{
    "version": "1.0.0",
    "actor": {
        "objectType": "Agent",
        "name": "madmin",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```

### Verb

The Verb, [evaluated](/vocabulary.md#verbs) describes the action of evaluating a learning activity.

``` javascript
 "verb":{
        "id":"http://www.tincanapi.co.uk/verbs/evaluated",
        "display":{
            "en":"evaluated"
         }
    },
    "result":{
        "score":{
            "raw":8
        },
        "completion":true
    }
``` 

### Object
The object defines the activity that has been evaluated.   

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
			}
		}
		
```



### Context



[Platform](/common_statements.md#context) identifies the platform, Moodle in this example.

[IP Address](https://registry.tincanapi.com/#uri/extension/310) is used to identify the client's real address as a Context extension.

SessionId is the VLE session Id

contextActivities has a context type of grouping. A course that relates to a assignment as the parent.

Plugin specific extensions are optional and not part of the core recipe.


``` javascript
"context": {
	"contextActivities":{
            "grouping":[
                {
                    "objectType":"Activity",
                    "id":"http://moodle.data.alpha.jisc.ac.uk/course/view.php?id=4",
                    "definition":{
                        "type":"http://adlnet.gov/expapi/activities/course",
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
        "extensions": 
 			"http://xapi.jisc.ac.uk/extensions/sessionId": { 
                "sessionId": "32456891"  
             },
            "http://id.tincanapi.com/extensions/ip-address": {  
                "ip-address":"10.3.3.48"
              }
        }
```


### Complete VLE Specific Examples
[Blackboard Example](/vle/blackboard/asssignment_graded.json)

[Moodle Example](/vle/moodle/asssignment_graded.json)