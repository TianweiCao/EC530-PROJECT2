# EC530-PROJECT2
## Hospital Chatroom User Stories
Add users to the system:  
Users who have registed in the system can chat in a chat room    
Each user can login, logout
all the message sent by other online users will be shown on each users' screeen
## Administrator User Stories
Add users to the system:  
Users should be added to the system and cannot register before being added to the system    
Assign and Change Roles to users  
  * Patient  
  * Nurse  
  * Doctor  
  * Admin  
  * Family member  


A user can have different roles, e.g.,   
a user can be a patient and/or a doctor  
A user can be a family member and/or a patient  
Provide interfaces to third party medical device makers (Thermometer, Pulse, Blood pressure, Glucometer, etc.) to have their devices feed data to the system  
Ability to disable or enable any device maker or application developer  
## Medical Professional (MP) User Stories
Browse Patients    
Assign a medical device to a Patient    
Assign Alert and scheduling for medical measurement, e.g.,       
* Patient to measure blood pressure daily.  MP will receive an alert if it not done.   
* Temperature is higher or lower than a value.  MP will get an alert if the measurement is outside acceptable range  


MP can input data for any patient  
MP can chat with patients using text, voice or videos.  
MP can read transcripts of Patient uploaded videos and messages  
MP can search for keywords in messages and chats  
MP have a calendar where they can show open time slots for appointments  
MP can see all appointments booked at any time  


## Introduction
This program can be devided into two parts, the first part is the Human-Computer Interface, it contains all element that are visionable to users. To be specific, it contains all the html pages that support log in, make appointment, check diagnose result and other operations.

The second part of this system is the Service Interface, it generates the service end and all database related parts such as mysql or mongoDB.

### The Chatroom Interface
In this project, we build a p2p chat program writtern in python. This program uses a C/S (client/server side) mode, which includes two parts: the server and client program. The client sends the message to the server, which forwards the chat message to other online users.

### Module Environment 

* Module Name: Hospital Chatroom
* Project Mode: C/S
* Windows 7, python 3, PyCharm 
* Python GUI, Multithread programming, Network programming, Database programming 

### Overview 
The program has client side and server side. The client side is operated by GUI, while the server side recieving incomming requests from clients wanting to communicate. 

First to start the server program to get link with the client. Then the client launcher will open the login window.

![??????](https://user-images.githubusercontent.com/70667153/114881111-48fe1b00-9e35-11eb-8494-6ceefed492bc.JPG)

Login Success!

![????????????](https://user-images.githubusercontent.com/70667153/114881153-51eeec80-9e35-11eb-917d-82da9556e59b.JPG)

Login Failed

![????????????](https://user-images.githubusercontent.com/70667153/114881164-54e9dd00-9e35-11eb-8b8e-9c3aad9a0380.JPG)

After the program login successfully, the user will get into the chat room window.

![??????????????????nickname ???????????????????????????????????????????????????](https://user-images.githubusercontent.com/70667153/114881179-587d6400-9e35-11eb-9bba-941eb0090253.JPG)
![??????????????????me?????????????????????](https://user-images.githubusercontent.com/70667153/114881200-5ca98180-9e35-11eb-80d5-ff618ae89593.JPG)

Then, the user can enter the message in the input box and send it to other online users. When multiple people getting online, the message will be sent to all online users at the sametime.

### The Building Strategy of this module
This chat module is based on a simulation of Socket Connection. To be specific, we make use of Socket api in python and devide our chatroom into two modules, the Client Part and the Server Part.

#### The Server Part
This part uses multiple threads to process clients' request. There are mainly three kinds of requests: login request, logout request and chat request. Whenever Server recieves a new request from client it start a new thread to process it. In other word, the server itself won't save any information.
#### The request code and response code
To process request and make response. We should at first design a protocol for request code and response code. To be specific, we have three kind of requests, so we set the first three number in request code as request type. 

* 000: login request
* 001: chat request
* 010: logout request

Besides this, we need one bit status number to show whether this user has been successfully login if so, the number is set to 1 else the number is 0.

We also need to design the content of response and request code. When we request for login, the content of our code should be user's socket number and his or her ID and pass word. If we request for sending message, the content of our code should be the message we want to send.   


The Server part shall also be connected to a database. We use the database to save ID and Password of all login users. In this case, when we process a login request, what we do is we check if we can find this user in the database.



## The Structure of Administrator
## The Service Interface
![Administrator System (2)](https://user-images.githubusercontent.com/78243340/153801472-8fb868b7-0cda-4c50-a2a5-cf8c332a00c7.jpg)  
This picture shows the structure of my service interface.
### People
Relation People is an outer database containing information of citizens, it can be realized by getting legally access to the database of government.  
This database contains ID, name and gender of a citizen. Where ID is the  major key.
### Patient
Relation Patient contains the information of patients, it is a private database maintained by hospital. Everyone who wants to make an appointment should create a patient account with his or her name, age, gender and ID. Each patient is assigned a PID as majot key.
### Staff
Relation Staff contains the information of staffs, it is a private database maintained by hospital. Each staff of hospital should have a staff account with his or her name, age, gender, ID,Birth, address and phone number. Each staff has a unique SID. Staff's account also specifies his or her duty and sector.
### Sector
This relation contains the information of sectors in hospital.
### Duty
This relation contains duty of a staff.
### Appointment
Every account in Patient database can make appointment, appointments are saved in Appointment database. The database specifies the date of appointment as well as the information of a patient. The major key of this database is AID.
### Appointment Type
To make the system more flexible, my system surpport a Appointment Type database. It specifies the type of each appointment.Each operation in Appointment database will result in changes in Appointment Type.
### Appointment Calendar
This database shows the number of appointment avaliable for a specific type everyday, the major key of this database is Date and AType. The system will first check if an specific appointment is availiable before adding it into the Appointment database. Each operation in Appointment database will result in changes in Appointment Calendar.
### Diagnose
Appointment will be processed and it result is saved in Diagnose database, this database contains diagnoses from doctors and may lead to Physical Examination. The major key of this database is DID.
### Physical Examination
Appointments for Physical Examination are saved in Physical Examination database, it specifies the type and date of examination. Before an Appointment is made, system should check Equipment relation to see if specific machine is avaliable.
### Medical Equipment Management
This database assign equipment for each examination, it connect the Physical Examination database and Equipment database.
### Equipment
This database shows the avaliability of equipments.
### Blood Pressure
This database contains the result of Blood Pressure test.
### Pulse
This database contains the result of Pulse test.
### Glucometer
This database contains the result of Glucometer test.
### Thermometer
This database contains the result of Thermometer test.

## The construction of Administrator system
When it comes to the construction of my system, I make some simplications on my design.

The Administrator system can be devided into three parts: the patient part, the doctor part and the administor part.

### Patient part
This part deal with the following request: 
* patients are able to login.
* patients are able to regist.
* patient are able to make an appointment.

## Login
![patientlogin](https://user-images.githubusercontent.com/78243340/158717469-e99f2425-f2e2-4727-9dc7-1d6084b26e0e.JPG)
We maintain a database to save information of patients. When a user wants to login as patient, this api will check if he or she is in the database.
![loginfail](https://user-images.githubusercontent.com/78243340/158717870-9f6c5eb6-dc6c-4330-9e1c-9397af805fa1.JPG)

## Regist
A user can add their information into the database by go to the regist page.
![regist](https://user-images.githubusercontent.com/78243340/158718041-c06e23f9-efdd-4e6d-879b-8c4ae4a8b98b.JPG)
He or she can either regist as patient or regist as relatives.
![resgistform](https://user-images.githubusercontent.com/78243340/158718701-e90b3a0f-69ea-41ec-a0a9-b48d270ff36b.JPG)
When finish registration, one's information will be add to patient form
![patient form](https://user-images.githubusercontent.com/78243340/158718735-e4f54b25-db20-4053-b95d-2d0f3eed1bfa.JPG)

## Make appointment
A user can make appointment, they can view all the doctors in the system, and how many patient are availiable for each doctor.
![appointmentform](https://user-images.githubusercontent.com/78243340/158733201-9157a1bf-9e4a-41ee-ba02-20b438880a89.JPG)
Patient can view his or her appointments in appointment date page
![appointmentdate](https://user-images.githubusercontent.com/78243340/158723588-95a98666-db72-4500-8d65-1ffe8e3e12f7.JPG)

### Doctor part
In this part, a doctor can do the following things:
* doctors are able to login.
* doctos are able to regist.
* doctors are able to see all appointments asigned to them.
* doctors are able to call next patient for treatment.

## doctor login
If a doctor has successfuly resgist, his or her information will be saved in database. Then he or she can login to the system.
![doctorlogin](https://user-images.githubusercontent.com/78243340/158734674-3341dfa1-8343-4edb-8691-9fbd38b02c2c.JPG)
![databaseform](https://user-images.githubusercontent.com/78243340/158735303-91899158-e423-40ee-adaa-9a06b6681de2.JPG)

## doctor regist
A user can go to the regist page to regist as a doctor.
![doctorregist](https://user-images.githubusercontent.com/78243340/158735842-e59c4d84-9f22-4f0b-bc47-bab8954572a8.JPG)
![regist2](https://user-images.githubusercontent.com/78243340/158735912-e22b2144-5f24-46ca-8dad-9d69cf12a379.JPG)

## doctor duty
A doctor can view all his or her patients.
![view](https://user-images.githubusercontent.com/78243340/158736528-da9330c0-0987-4e6f-92d0-2ed0d3f00751.JPG)
A doctor can treat his or her patient and is able to call them one by one.
![call](https://user-images.githubusercontent.com/78243340/158736662-a402ff96-8c38-491f-988b-df0adf297a79.JPG)

### Administrator part
This part alongs administrator to manage the whole system:
* Administrator are able to login.
* Administrator are able to regist.
* Administrator is able to add or delete doctors.
* Administrator is able to set the number of patients each doctor shall treat each day.
* Administrator is able to add or delete new sectors for the system.

## administrator login
![adlogin](https://user-images.githubusercontent.com/78243340/158741038-21695bba-e30f-4f69-97b8-3fb37c74cfb1.JPG)
![for???](https://user-images.githubusercontent.com/78243340/158741120-953172cb-2400-4a89-b4ce-21863df74b62.JPG)
## administrator regist
![password](https://user-images.githubusercontent.com/78243340/158742278-b5a6f1bf-ac56-44af-895c-70124d329bd5.JPG)
It will throw exception if two password are not the same
![error](https://user-images.githubusercontent.com/78243340/158742421-7c88f98d-e0ba-44f1-a953-bb325ccbecd9.JPG)

## doctor management
Administrator can add or delete doctors, he or she has directly access to doctor database.
![adddoc](https://user-images.githubusercontent.com/78243340/158742933-92675024-0ff9-4064-b915-d22043909fe4.JPG)
![doc2](https://user-images.githubusercontent.com/78243340/158743191-86431f23-d780-4be3-958d-d9deb61e5d3c.JPG)

## sector management
Administrator can add or delete sectors, he or she has directly access to sector database.
![sector](https://user-images.githubusercontent.com/78243340/158743344-92fab23e-1203-4351-8699-68dd9697a25f.JPG)

## the management of whole system
Administrator can view the whole system.
![whole](https://user-images.githubusercontent.com/78243340/158743506-98307d00-38b3-4e2c-8539-6437215ececd.JPG)

### Regulation of database 
Administrator table
![admin](https://user-images.githubusercontent.com/78243340/158744556-ba9f0c3f-1dbc-4e50-b5d7-251d63f83a40.JPG)

Doctor table
![doctor](https://user-images.githubusercontent.com/78243340/158744992-a7466d3a-6003-4815-87d2-09d25b080bac.JPG)

Patient table
![patient](https://user-images.githubusercontent.com/78243340/158745048-5cf2bd3c-d25e-4784-adab-459f0c709742.JPG)

Section table
![section](https://user-images.githubusercontent.com/78243340/158745133-5bd39221-a241-4560-a554-40b9bfc6d0e2.JPG)






