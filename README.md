# json powerDB a project to link a student from to a server Database
### This project is created in order to understand the basic CRUD operations of json powerDB
##### The Put Command:
It is is an IML(Index manipulation) Command. It reads the record and puts/Insert them into the JasonDB.
1. It needs token that is connection token of the database where you wand to add the details for the new student. 
2. It needs the dbname i.e that specific database name where you want to insert the new record.
3. It needs the rel name that is the realation name where youwant to add the new records.
4. JsonStr The actual content of that record.

```
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

