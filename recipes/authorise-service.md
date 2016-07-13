#Authorisation Recipe
Revision: 0.1 

## Purpose
This activity records a service authorising authorisation a person.

DRAFT:
A service may authorize a person to access an application. In which case the actor is the service, the object is the person, and the target is the application. 

Q) what is the xapi element equivilent to 'target'?

## Definition
### Actor
 

q) would be the identity provider?
``` Javascript
{
    
}
```

### Verb

``` javascript
"verb": {
        "id": "http://activitystrea.ms/schema/1.0/authorize",
        "display": {
            "en": "authorise"
        }
    },
```


### Object

In this case, object is the person that has been given access to a resource. 


<table>
	<tr><th>Property in Example</th><th>Description</th></tr>
	<tr>
		<td>object.objectType</td>
		<td>"Agent"</td>
	</tr>
	<tr>
		<td>object.name</td>
		<td>Full name of user, optional.</td>
	</tr>

		<tr>
		<td>object.account</td>
		<td>JSON Object with unique id(account.name) and home page(account.homepage)</td>
	</tr>
</table>

``` Javascript
{
    "object": {
        "objectType": "Agent",
        "name": "John Smith",
        "account": {
            "name": "2",
            "homePage": "https://courses.alpha.jisc.ac.uk/moodle"
        }
    },
```


