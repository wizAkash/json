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

```
{
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

## The Save student function
This function is the heart and core of this project it basically call all other required function in order to validate data and
transffers the record to the data base

```javascript
function saveStudent() {
                var jsonStr = validateAndGetFormData();
                if (jsonStr === "") {
                    return;
                }
                var putReqStr = createPUTRequest("90938612|-31948826027903061|90944302",
                        jsonStr, "SAMPLE", "EMP-REL");
                alert(putReqStr);
                jQuery.ajaxSetup({async: false});
                var resultObj = executeCommandAtGivenBaseUrl(putReqStr, "http://api.login2explore.com:5577", "/api/iml");
                jQuery.ajaxSetup({async: true});
                alert(JSON.stringify(resultObj));
                resetForm();
            }
```

## The validateAndGetFormData()
This function will basically look if all the necessary details has been entered or not and if they are it will return that as a string type which will get 
stored in the jsonStr variable. And if they are not it will return the empty string alerting the user to enter those required fields.

```javascript
function validateAndGetFormData() {
                var stuIdVar = $("#stuId").val();
                if (stuIdVar === "") {
                    alert("Student ID Required Value");
                    $("#stuId").focus();
                    return "";
                }
                var stuNameVar = $("#stuName").val();
                if (stuNameVar === "") {
                    alert("Student Name is Required Value");
                    $("#stuName").focus();
                    return "";
                }
                var stuEmailVar = $("#stuEmail").val();
                if (stuEmailVar === "") {
                    alert("Employee Email is Required Value");
                    $("#stuEmail").focus();
                    return "";
                }
                var stuMobVar=$("#stuMobile").val();
                if (stuMobVar==""){
                    alert("Student mobile number is required");
                    S("#stuMobile").focus();
                    return "";
                }
                var stuSubVar = $("#stuSub").val();
                if (stuSubVar === "") {
                    alert("Subject Selection is a Required Value");
                    $("#stuSub").focus();
                    return "";
                }
```

## The executeCommandAtGivenBaseUrl() function
This function will put all the data which has been entered by the student to the database whose url has been used in the code. It will take three arguments
the request of the data to put it on the database, the base url and ent end url. Definition of this function is available at the jsson commonjs.

## The resetForm() function
This function will will refresh the form back to empty after the successful submission of the details of the previous student.

```javascript
function resetForm() {
                $("#stuId").val("");
                $("#stuName").val("");
                $("#stuEmail").val("");
                $("#stuMobile").val("");
                $("#stuSub").val("");
                $("#stuId").focus();
            }
```
