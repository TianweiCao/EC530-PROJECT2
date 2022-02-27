# EC530-PROJECT2
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
