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

