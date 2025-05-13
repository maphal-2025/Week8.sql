# Week8.sql

erDiagram
    Patients {
        INT PatientID PK
        VARCHAR(100) Name NOT NULL
        DATE DateOfBirth NOT NULL
        VARCHAR(15) Phone UNIQUE
        VARCHAR(100) Email UNIQUE
        TEXT Address
    }

    Doctors {
        INT DoctorID PK
        VARCHAR(100) Name NOT NULL
        VARCHAR(100) Specialty NOT NULL
        VARCHAR(15) Phone UNIQUE
        VARCHAR(100) Email UNIQUE
    }

    Appointments {
        INT AppointmentID PK
        INT PatientID NOT NULL
        INT DoctorID NOT NULL
        DATETIME AppointmentDate NOT NULL
        ENUM Status "Scheduled, Completed, Cancelled"
    }

    Medical_Records {
        INT RecordID PK
        INT PatientID UNIQUE NOT NULL
        TEXT Diagnosis
        TEXT Prescriptions
        TIMESTAMP LastUpdated DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
    }

    Patients ||--o{ Appointments : has
    Doctors ||--o{ Appointments : has
    Patients ||--o{ Medical_Records : has
