#Authorisation Recipe
Revision: 0.1

## Purpose
This activity records a person authorizing a request

## Definition


### Actor

In this case the actor is the person authorizing the request.

``` Javascript
{
    
}
```

### Verb

The Verb,[http://activitystrea.ms/schema/1.0/authorize](/vocabulary.md#verbs) 

Indicates that the actor has authorized the object. If a target is specified, it means that the authorization is specifically in regards to the target. For instance, a service can authorize a person to access a given application; in which case the actor is the service, the object is the person, and the target is the application. In contrast, a person can authorize a request; in which case the actor is the person and the object is the request and there might be no explicit target.

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/authorize",
        "display": {
            "en": "authorise"
        }
    },
```


### Object
The object is an account object of the person.

In the account object, the homePage is the canonical home page for the system the account is on and name is the unique id being used to log on. 


``` javascript

"object":{
		"objectType": "Agent",
		"account": {
			"homePage": "http://www.example.com", //IRL
			"name": "2425" //String
			
		}
	}	
```

