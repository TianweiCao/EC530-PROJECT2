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

![捕获](https://user-images.githubusercontent.com/70667153/114881111-48fe1b00-9e35-11eb-8494-6ceefed492bc.JPG)

Login Success!

![登陆成功](https://user-images.githubusercontent.com/70667153/114881153-51eeec80-9e35-11eb-917d-82da9556e59b.JPG)

Login Failed

![登陆失败](https://user-images.githubusercontent.com/70667153/114881164-54e9dd00-9e35-11eb-8b8e-9c3aad9a0380.JPG)

After the program login successfully, the user will get into the chat room window.

![上方显示的是nickname 右边的滚动条如果消息很多可以向下滚](https://user-images.githubusercontent.com/70667153/114881179-587d6400-9e35-11eb-9bba-941eb0090253.JPG)
![自己说的话是me别人说的是昵称](https://user-images.githubusercontent.com/70667153/114881200-5ca98180-9e35-11eb-80d5-ff618ae89593.JPG)

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



### The Structure of Administrator
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

### Overview 
To get started, I first build a database to save all users. Also build html page to surpport login and regist.
![one](https://user-images.githubusercontent.com/78243340/158317731-45bda412-d1b6-4b5b-8ead-86ae905a90e6.JPG)
![two](https://user-images.githubusercontent.com/78243340/158317750-6f12c3df-432d-4db3-9039-66a1ac299416.JPG)
![three](https://user-images.githubusercontent.com/78243340/158317756-cfe8e543-c3a3-4a22-9614-a3f92bfb3ec0.JPG)
![four](https://user-images.githubusercontent.com/78243340/158317769-49a4aa84-4dbf-4988-bd17-5563effa806c.JPG)
![five](https://user-images.githubusercontent.com/78243340/158317782-006adecc-9af2-46b3-86ab-3b0447ae1ab5.JPG)

