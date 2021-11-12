# json powerDB a project to link a student form to a server Database

## This project is created in order to link a students details to a specific json database.

*The main objective of this project is to create a web form which will ask for the **students details** and send them to jsonpowerdb in a specific database.
So, It's really important to know about the jsonpowerdb.*

### Benefits of using Json power DB
1. Simplest way to retrieve data in a JSON format.
2. Schema-free, Simple to use, Nimble and In-Memory database.
3. It is built on top of one of the fastest and real-time data indexing engine - PowerIndeX.
4. It is low level (raw) form of data and is also human readable.
5. It helps developers in faster coding, in-turn reduces development cost.


### The CRUD operations
##### The Put Command:
It is is an IML(Index manipulation) Command. It reads the record and puts/Insert them into the JasonDB.
1. It needs token that is connection token of the database where you wand to add the details for the new student. 
2. It needs the dbname i.e that specific database name where you want to insert the new record.
3. It needs the rel name that is the realation name where youwant to add the new records.
4. JsonStr The actual content of that record.

```javascript
{
    "token": "90938612|-31948826027903061|90944302",
    "cmd": "PUT",
    "dbName": "Student",
    "rel": "stu-rel",
    "jsonStr": {
        "name": "Isha",
        "email": "isha@gmail.com",
        "occupation": "student",
      "mobile":7898765465,

    }
}
```

##### The Get Command:
It is an IRL(Index retrievel) Command. It reads the alredy present records from the JasonDb and displays the content of that record.
1. 1. It needs token that is connection token of the database from where you wand to get the details for the student. 
2. It needs the dbname i.e that specific database name from where you want to get the record.
3. It needs the rel name that is the realation name from where you want to get the records.
4. JsonStr It will specify that which record you want to see.

```
{
    "token": "90938612|-31948826027903061|90944302",
    "dbName": "Student",
    "cmd": "GET",
    "rel": "stu-rel",
    "jsonStr": {
        "name": "Isha ",
    }

}
```


##### The update Command:
It is an IML(Index manipulation) Command. It updates any record which is already present in the database. In case you want to update any record you can use this command.
1. 1. It needs token that is connection token of the database in which you wand to update the details for the student. 
2. It needs the dbname i.e that specific database name in which you want to update the record.
3. It needs the rel name that is the realation name in which you want to update the records.
4. JsonStr It will specify that which record you want to update by taking the record number and then the updated data.

```{
    "token": "90938612|-31948826027903061|90944302",
    "dbName": "Student",
    "cmd": "UPDATE",
    "rel": "stu-rel",
    "jsonStr": {
      "1":{"mobile":3424567431},
      "2":{"name":"Meena",
           "email":"meenajulka@gmail.com",
          }
    }

}

```

#### The remove Command:
It is an IML(index manipulation) Command. It removes some certain record from the database.
1. 1. It needs token that is connection token of the database in which you want to delete the record of some certain student. 
2. It needs the dbname i.e that specific database in which you want to delete the record of some certain student.
3. It needs the rel name that is the realation name in which you want to delete the record of some certain student.
4. record  It will specify the record number which you want to delete.

```
{
    "token": "401400726|-363956312424328770|401400726",
    "cmd": "REMOVE",
    "dbName": "Student",
    "rel": "stu-rel",
    "record": 1
}
```

### Linking a html form to a data base
*We'll Create a web form and will connect it to the json db such that if some one enters the details in that form it will get reflected to the database as well.
We'll use XMLHTTPS in order to send the respond to the jsondb through the web browser. 
Javascript will be playing a huge role in order to write some important functions to fetch the data entered in the form and send it to the database.*

