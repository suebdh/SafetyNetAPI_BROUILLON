# SafetyNetAPI

Backend API for SafetyNet Alerts application, developed as part of the OpenClassrooms Java developer curriculum.

## Description

**SafetyNetAPI** is a REST API implemented with Spring Boot, designed to provide emergency services with relevant information about individuals in distress and their locations.
This application reads and stores data in a JSON file and exposes endpoints to retrieve and update this information.
Its primary goal is to send crucial data to emergency service systems efficiently.

## Tech Stack

- Java 11+
- Spring Boot
- Maven (preferred, but Gradle is also possible)
- Git for version control
- Java library for JSON parsing (e.g., Jackson or Gson)
- Unit testing with JUnit
- Code coverage measured with JaCoCo
- Logging (execution traces) with Log4j

## Usage

- Clone the repository
- Build with Maven: `mvn clean install`
- Run the application

## API Endpoints

### GET Endpoints

- `GET http://localhost:8080/firestation?stationNumber=<station_number>`  
  Returns a list of people covered by the specified fire station number. The response includes first name, last name, address, phone number, and a count of adults and children (18 years or younger) in the area.

- `GET http://localhost:8080/childAlert?address=<address>`  
  Returns a list of children (18 years or younger) living at the given address, including their first name, last name, age, and a list of other household members. Returns an empty string if no children are found.

- `GET http://localhost:8080/phoneAlert?firestation=<firestation_number>`  
  Returns a list of phone numbers of residents covered by the specified fire station, used for sending emergency text messages.

- `GET http://localhost:8080/fire?address=<address>`  
  Returns a list of residents at the given address along with the fire station number serving that address. Includes name, phone number, age, and medical records (medications, dosages, allergies).

- `GET http://localhost:8080/flood/stations?stations=<list_of_station_numbers>`  
  Returns a list of households served by the specified fire stations, grouped by address. For each person, includes name, phone number, age, and medical records.

- `GET http://localhost:8080/personInfo?lastName=<lastName>`  
  Returns the name, address, age, email, and medical records for each person with the specified last name. Multiple persons with the same last name will all be listed.

- `GET http://localhost:8080/communityEmail?city=<city>`  
  Returns the email addresses of all residents in the specified city.

---

### POST / PUT / DELETE Endpoints

- `POST/PUT/DELETE http://localhost:8080/person`  
  Add a new person  
  Update an existing person (assumes first and last names do not change, other fields can)  
  Delete a person (unique identifier is first name + last name)

- `POST/PUT/DELETE http://localhost:8080/firestation`  
  Add a fire station to address mapping  
  Update the fire station number for an address  
  Delete a fire station or address mapping

- `POST/PUT/DELETE http://localhost:8080/medicalRecord`  
  Add a medical record  
  Update an existing medical record (assumes first and last names do not change)  
  Delete a medical record (unique identifier is first name + last name)