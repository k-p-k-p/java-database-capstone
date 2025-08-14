# Smart Clinic Schema Design

## MySQL Database Design

### Table: patients
- `id`: INT, Primary Key, AUTO_INCREMENT
- `name`: VARCHAR(100), NOT NULL
- `email`: VARCHAR(100), NOT NULL, UNIQUE
- `phone`: VARCHAR(15), NOT NULL

---

### Table: doctors
- `id`: INT, Primary Key, AUTO_INCREMENT
- `name`: VARCHAR(100), NOT NULL
- `specialization`: VARCHAR(100), NOT NULL
- `email`: VARCHAR(100), NOT NULL, UNIQUE

---

### Table: appointments
- `id`: INT, Primary Key, AUTO_INCREMENT
- `doctor_id`: INT, NOT NULL, Foreign Key → doctors(id)
- `patient_id`: INT, NOT NULL, Foreign Key → patients(id)
- `appointment_time`: DATETIME, NOT NULL
- `status`: INT (0 = Scheduled, 1 = Completed, 2 = Cancelled)
---

### Table: admin
- `id`: INT, Primary Key, AUTO_INCREMENT
- `username`: VARCHAR(50), NOT NULL, UNIQUE
- `password`: VARCHAR(255), NOT NULL

---

## MongoDB Collection Design

### Collection: prescriptions
```json
{
  "_id": "ObjectId('64f1a9c3a12b4f567890abcd')",
  "appointmentId": 105,
  "patientId": 22,
  "medication": "Amoxicillin",
  "dosage": "500mg, twice daily",
  "notes": "Take after meals and complete the full course.",
  "tags": ["antibiotic", "urgent"],
  "metadata": {
    "createdBy": "Dr. Anita Rao",
    "createdAt": "2025-08-14 09:30"
  }
}
