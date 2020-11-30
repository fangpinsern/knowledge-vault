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

For example, when the application gets bigger, you are bound to have more and more controllers. Imagine looking throught 20 controllers at the side of your IDE. You might say "Just use the search". But are you gonna really remember the names of all 20 controllers?

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
