# Nexus Care Hospital Management System (College Java Mini Project)

## Project Overview
This is a comprehensive Java Mini Project built with **Java (JDBC) + MySQL Database** demonstrating Object-Oriented Programming (OOP) and Relational Database Management System (RDBMS) principles for university/college submissions and laboratory vivas.

---

## Architecture & Modules
- **`com.medicare.HospitalManagementSystem`**: Main entry console with multi-role authentication (Admin, Receptionist, Doctor).
- **`com.medicare.modules.AdminModule`**:
  - `addDoctor` / `addReceptionist`: SQL `INSERT` into staff and user credentials.
  - `deleteDoctor` / `deleteReceptionist`: SQL `DELETE` for staff departures.
  - `monitorOperations`: SQL `SELECT` for overall inpatients, available beds, and total revenue.
  - `viewDischargedPatients`: Master SQL `SELECT` view of all treated, billed, and discharged patients.
- **`com.medicare.modules.ReceptionistModule`**:
  - `registerPatient`: SQL `INSERT` generating unique `pat-xxx` ID.
  - `bookAppointment`: SQL `INSERT` linking Patient ID to Doctor ID & slot.
  - `allocateBed`: SQL `UPDATE` changing bed from `Available` to `Occupied`.
  - `dischargePatient`: **3-in-1 Atomic Transaction** (Calculate total bill `INSERT`, update patient to `Discharged` `UPDATE`, and release bed back to `Available` `UPDATE`).
- **`com.medicare.modules.DoctorModule`**:
  - `viewDailySchedule`: SQL `SELECT` filtering appointments by doctor ID and today's date.
  - `checkMedicalHistory`: SQL `SELECT` fetching all previous diagnoses, visits, and medications for any Patient ID.
  - `writePrescriptionAndDiagnosis`: "Save Record" SQL `UPDATE` attaching doctor notes, disease name, and prescribed medicines.
- **`com.medicare.db.DBConnection`**: JDBC Connection manager for MySQL (`hospital_db`).

---

## How to Run in Eclipse / IntelliJ / NetBeans
1. Install **MySQL Server** (or start XAMPP / WampServer).
2. Open MySQL Workbench, phpMyAdmin, or terminal:
   ```sql
   source schema.sql;
   ```
3. Open `java-hospital-project` in your favorite Java IDE (IntelliJ IDEA / Eclipse / VS Code).
4. Add `mysql-connector-j-8.x.x.jar` to project build path / dependencies.
5. In `DBConnection.java`, verify MySQL password (default: `root` / `root`).
6. Run `HospitalManagementSystem.java` as a Java Application!

---

## Sample Credentials for Viva Demo
- **Admin**: `admin@medicare.com` / `admin123`
- **Receptionist**: `reception@medicare.com` / `reception123`
- **Doctor (Dr. Alok Nath)**: `alok.nath@medicare.com` / `doctor123`
