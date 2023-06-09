﻿# delivery-application-ui

To view the preview page [please CLICK HERE](http://delivery-application.s3-website-eu-west-1.amazonaws.com/).<br/>

# 🤔 What is the purpose of this application?
This project written in Java language and Spring Framework, represent Implementation of a Delivery API containing the following functionality:<br/>

### 💬 Timeslot
A delivery window containing start time, end time and supported addresses.<br/><br/>
👉 The two sources below will be fetched in parallel in order to validate the resulted timeslots:<br/>
• A local static json file named `'courierAPI.json'` is loaded when the program is starting. This file contains the available timeslots for the upcoming week.<br/>
• Courier timeslots that fall on holidays will be excluded. For this part I have used HolidayAPI (https://holidayapi.com/docs).<br/>

👉 Each timeslot can be used for 2 deliveries.

### 💬 Delivery
Contains status & selected timeslot.
Business capacity - the system supports up to 10 deliveries per day.
To make sure that the system supports 10 deliveries per day, I used Github's library named Bucket4j.

### 💬 Address
I have used Geoapify API to locate correct addresses (https://www.geoapify.com/geocoding-api) into an object that holds the address data (such as: street, line1, line2, country, postcode, etc...).

# Extra Details
NOTE: This program is really simple, at this moment the program does not support concurrent requests. These days I am working on a new project to upgrade this one by using Spring WebFlux To handle concurrent requests.

## External API I have used in this project
Geoapify (https://www.geoapify.com/geocoding-api)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
To locate correct addresses.<br/><br/>
HolidayAPI (https://holidayapi.com/docs)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
To exclude holidays from timeslots.<br/><br/>
Bucket4j Github's library<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
To manage system delivery capacity per day.

# Endpoints

### 👉 TimeslotController:

#### POST: retrieveAllAvailableTimeslots (Address address)
| Parameter | Type      |
| :-------- |:----------|
| `address` | `Address` |
```http
 http://localhost:8080/api/timeslots
```

### 👉 AddressController:

#### POST: resolveAddress(String searchTerm)
| Parameter | Type      |
| :-------- |:----------|
| `searchTerm` | `String` |
```http
 http://localhost:8080/api/resolve-address
```
### 👉 DeliveryController:

#### POST: bookDelivery(CreateDeliveryDto createDeliveryDto)
| Parameter | Type      |
| :-------- |:----------|
| `createDeliveryDto` | `CreateDeliveryDto` |
```http
 http://localhost:8080/api/deliveries
```

#### POST: completeDelivery(Long deliveryId)
| Parameter | Type      |
| :-------- |:----------|
| `deliveryId` | `Long` |
```http
 http://localhost:8080/api/deliveries/{deliveryId}/complete
```

#### DELETE: cancelDelivery(Long deliveryId)
| Parameter | Type      |
| :-------- |:----------|
| `deliveryId` | `Long` |
```http
 http://localhost:8080/api/deliveries/{deliveryId}
```

#### GET: getAllDailyDeliveries()
| Parameter | Type   |
|:----------|:-------|
| `none`    | `none` |
```http
 http://localhost:8080/api/deliveries/daily
```

#### GET: getAllWeeklyDeliveries()
| Parameter | Type      |
| :-------- |:----------|
| `none` | `none` |
```http
 http://localhost:8080/api/deliveries/weekly
```

# 🛠 Tech Stack
Language & Framework:
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Java
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Spring Framework
<br/>

Database:
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
SQL
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
MySQL
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Spring Hibernate JPA (SQL)
<br/>

Libraries and External API’s:
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Geoapify (https://www.geoapify.com/geocoding-api)
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
HolidayAPI (https://holidayapi.com/docs)
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Bucket4j Github's library
<br/>

Caching & Scheduling Mechanisms:
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Spring Scheduling
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Spring Hibernate JPA + MySQL as a local cache memory
<br/>

Client-Side UI:
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
HTML
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
CSS
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
Bootstrap 5
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
JavaScript
<br/>

<br/>
Thanks for reading,
<br/>
Chelly 👩🏻‍💻
