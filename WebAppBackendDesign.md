# Designing the Backend of a Web App

## Introduction

---

The backend of a website is a portion of the website people usually do not see.

It does a few key functions:

1. Serves data from the database to the relevant services
2. Organise and compute data before being sent
3. Authorization and authentication services
4. Many more

There are many ways to design the backend of your application. Here are some things I feel are important when doing backend web development

## Controllers and Services

Controllers and services are very crucial when it comes to backend development. Services should have only 1 purpose which is to deal with a single type of data in a certain way. As much as possible, try not to mix the data types within services. This makes it very hard for the service to be reusable.

For example:  
Goal - Check if student is in a valid class

Data:  
Student  
Class

Services:  
getStudents - purpose is to get students information from the database  
getClasses - purpose is to get class information from the database

Controllers:  
checkIfStudentInValidClass - using the services, you can get the class information to cross check if the student is in a valid

As you can see, services only deal with a single data type. If the "getStudents" service were to have checked if the student was in a valid class, the service might be unusable to other controllers. Hence you will spend more time creating new services to suite the need of the controller.

At the end of the day, controllers should control the usage of the services whereas the services should serve what is needed.

Imagine going to a restraunt, asking the waitress what is the special today and the waitress tells you her life story. Nobody wants that.

## CRUD is King

CREATE - creates data

READ - gets data

UPDATE - updates data

DELETE - delete data

These 4 calls are sufficient to do almost anything. To build fast, build these 4 services. Afterwards, look how to optimize the APIs and bundle common API requests into 1 response. This will help you see what you need instead of building out things that you think you need but end up not needing wasting valuable time.

## File Structures

Always have a good folder structures. Having a messy and un-organised file structure can hamper your development when your projects get bigger.

For example, when the application gets bigger, you are bound to have more and more controllers. Imagine looking throught 20 controllers at the side of your IDE. You might say "Just use the search". But are you gonna really remember the names of all 20 controllers? Cou can try to group the folders together to clean it up.

Therefore, you should have a good folder structure. Every file and folder should be there for a reason. If they have no purpose, remove them.

Recommended File Structure:  
.  
|-- src/  
|&emsp;&emsp;|-- controllers/  
|&emsp;&emsp;|&emsp;&emsp;|-- individual controllers  
|&emsp;&emsp;|-- services/  
|&emsp;&emsp;|&emsp;&emsp;|-- individual services  
|&emsp;&emsp;|-- routes/  
|&emsp;&emsp;|&emsp;&emsp;|-- route files  
|&emsp;&emsp;|-- models/  
|&emsp;&emsp;|&emsp;&emsp;|-- database models files  
|-- index.js  
|-- README.md  
|-- .gitignore  
|-- package.json

## Documentation

Even though you need fast development, always try your best to have documentation. Even if it is just comments within the function explaining what that section is doing, or comments above the function explaining what the function does. This helps others who are maintaining your code understand what is going on.

For APIs, you should have proper documentation whenever possible. I would usually do it after I have tested the routes so I do not forget to do it. It does not have to be complex. Just certain key informations about the API will do.

This will help the users of your API understand how to use the API. Some examples of documentations are given below

### 1. GET Request

Description: Details of what this request does

Query parameters: What parameter are available for this get request. This would be great in table form.  
E.g.

| Key  | Type   | Description                    |
| ---- | ------ | ------------------------------ |
| name | string | name of the student            |
| id   | number | Unique ID given to the student |

Sample query: A sample query to help assist the users of the API  
Sample response: Response form the query used in the sample query

### 2. POST Request

Description: Details of that the request does

Body keys: What keys are required in the body and what is not required. Best if in table format.  
E.g.

| Key         | Type   | Required | Description                 |
| ----------- | ------ | -------- | --------------------------- |
| name        | string | yes      | name of the student         |
| classNumber | number | yes      | Class number of the student |

Sample body: A sample body sent to the backend  
Sample reponse: Response from the body posted to the backend

### 3.PUT Request

Description: Exactly what will be changed will occur.

Keys required in request body: What are the values required for the requrests. Are somethings optional? Certain values may not be allowed to change.
E.g.

| Key         | Type   | Required | Description                 |
| ----------- | ------ | -------- | --------------------------- |
| name        | string | yes      | name of the student         |
| classNumber | number | no       | Class number of the student |

Sample request URL: A sample of the API call  
Sample requrest body: Show what can be updated
Sample response: Response given by the server after request URL and request body sent

### 4. DELETE Request

Desctiption: What is the details of the delete. Would it remove other infoamtion as well? What are the relevant checks done? Is it permanent?

Sample request - Sample API call to delete objects  
Sample response - response from the delete call

\*\* Ideally, you should not delete any information on the database but instead set a flag to say that this information is deleted. This might not be ethical, but it improves performance as well as allow for restoration of backup feature to users.
