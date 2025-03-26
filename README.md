# Hospital_Management_System

![intro](https://github.com/Abhishekshaw2002/Hospital_Management_System/blob/b2d5114383ab6983e43e2a2860e643ed6725e0e7/img%20used/HMS.png)

# Problem Statement:
In the healthcare industry, managing patient information, medical records, and hospital resources is crucial. The current system of managing this data is either manual or semi-automated, leading to various challenges such as difficulty in accessing patient records, and inefficiencies in resource management. This project aims to check and solve these operations by implementing an SQL-based system to manage all aspects of hospitality services efficiently. 

# Objective:
The objective of this project is to centralized and develop an SQL -based Hospital Management System that simplifies billing, room allocations, department, patient’s relationship. This system will reduce human errors, and provide quick access to critical information for better decision making.

![intro](https://github.com/Abhishekshaw2002/Hospital_Management_System/blob/b2d5114383ab6983e43e2a2860e643ed6725e0e7/img%20used/Screenshot%202025-03-23%20200956.png)

# Technology Used in the Project:
•	SQL (Structured Query Language)
•	MYSQL as the database management system

# Scope of the Project :
The project will cover Patients, Doctors, Appointment, Medical Record, Billing, Departments, Staff, Room, Prescription, Medications, Surgeries, Lab Tests, Insurance, Nurses, Visits, Shift, Emergency Contacts, Ward, Admissions, Discharge, Ambulance, Feedback systems.

![intro](https://github.com/Abhishekshaw2002/Hospital_Management_System/blob/b2d5114383ab6983e43e2a2860e643ed6725e0e7/img%20used/Screenshot%202025-03-23%20203629.png)

# Components of the Project:
  1. Patient Management: Registering, updating, and managing Patient details.
  2. Room Management: Handling room details, availability, and pricing.
  3. Booking System: Facilitating room reservations and cancellations.
  4. Billing System: Generating invoices and handling payments.
  5. Doctor Management: Managing staff details and assignments.
  6. Feedback System: Collecting and analyzing customer feedback.

# ER-Diagram:
![intro](https://github.com/Abhishekshaw2002/Hospital_Management_System/blob/b2d5114383ab6983e43e2a2860e643ed6725e0e7/img%20used/ER%20Hospital.png)

# SQL queries and execution Results:

1. Find surgeries along with their details and costs.
SELECT 
    s.surgery_id, s.surgery_type,  s.surgeries_rate, p.first_name, p.last_name
FROM 
    Surgeries s
JOIN 
    Patients p ON s.patient_id = p.patient_id;


2. List all Patients with their room numbers.
SELECT Patients.first_name, Patients.last_name, Rooms.room_id
FROM Patients
JOIN Rooms ON Patients.room_id = Rooms.room_id;


3. List all details of patients' appointments including patient names, appointment IDs, appointment dates, doctor names, prescribed medications, dosages, and billing information, sorted by appointment date.
SELECT 
    p.first_name AS patient_first_name,  
    p.last_name AS patient_last_name,   
    a.appointment_id,  a.appointment_date, 
   d.first_name AS doctor_first_name, 
   d.last_name AS doctor_last_name,   
   pr.medication,  pr.dosage, 
    b.amount AS bill_amount, b.status AS bill_status

FROM 
    Patients p

JOIN 
    Appointments a ON p.patient_id = a.patient_id

JOIN 
    Doctors d ON a.doctor_id = d.doctor_id

JOIN 
    Prescriptions pr ON p.patient_id = pr.patient_id AND d.doctor_id = pr.doctor_id

JOIN 
    Medications m ON pr.prescription_id = m.prescription_id

JOIN 
    Billing b ON p.patient_id = b.patient_id AND a.appointment_id = b.appointment_id

ORDER BY 
    a.appointment_date;


4. List the all patient’s full names, and their corresponding lab test names and dates.
  SELECT
    Patients.patient_id,
    CONCAT(Patients.first_name, ' ', Patients.last_name) AS patient_name,
    LabTests.test_name,
    LabTests.test_date
FROM
    Patients
JOIN LabTests ON Patients.patient_id = LabTests.patient_id;


5. List all patient's full names, and their corresponding feedback details.
SELECT
    Patients.patient_id,
    CONCAT(Patients.first_name, ' ', Patients.last_name) AS patient_name,
    Feedback.feedback_id,  Feedback.rating, Feedback.feedback_date
FROM
    Patients
JOIN Feedback ON Patients.patient_id = Feedback.patient_id;


6. List the patient IDs, full names, and their corresponding billing amounts.
SELECT
    Patients.patient_id,
    CONCAT(Patients.first_name, ' ', Patients.last_name) AS patient_name,
    Billing.amount
FROM
    Patients
JOIN Billing ON Patients.patient_id = Billing.patient_id;


7. List all patient details and their corresponding ambulance details. 
SELECT
    Patients.patient_id,
    CONCAT(Patients.first_name, ' ', Patients.last_name) AS patient_name,
    Ambulances.ambulance_id,
    Ambulances.license_plate,
    Ambulances.driver_name
FROM
    Patients
JOIN Ambulances ON Patients.patient_id = Ambulances.patient_id;


# Challenges you faced in the project:
•	Integrating data from various sources such as patient records, billing systems, lab results, and appointment schedules.
•	Ensuring data integrity through proper use of foreign keys and constraints
•	Designing a user-friendly schema that is scalable for future needs.

	
# Future improvement scope:
•	Implement advanced analytics for patient behaviour and preferences.
•	Expanding telehealth services to allow remote diagnosis and treatment.
•	Integration with online booking platforms for real-time updates.
•	Regularly update the system to comply with new regulations and standards, and provide automated compliance checks.
•	Implement workflow automation tools to streamline processes such as patient admissions, discharge, billing, and inventory management.

# Conclusion:
The implementation of Hospital Management System (HMS) is essential in modernizing healthcare facilities and enhancing the overall patient experience. By integrating various modules such as patient records, billing, appointments, lab results, and more, Hospital Management System streamlines hospital operations, reduces administrative burdens, and improves the efficiency of healthcare delivery.





