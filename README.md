

class Patient:
    def __init__(self, name, age):
        self.name = name
        self.age = age

class Doctor:
    def __init__(self, name, specialty):
        self.name = name
        self.specialty = specialty

class Appointment:
    def __init__(self, patient, doctor, date):
        self.patient = patient
        self.doctor = doctor
        self.date = date

class HospitalManagementSystem:
    def __init__(self):
        self.patients = []
        self.doctors = []
        self.appointments = []

    def add_patient(self, name, age):
        patient = Patient(name, age)
        self.patients.append(patient)
        print(f"Patient '{name}' added successfully.")

    def add_doctor(self, name, specialty):
        doctor = Doctor(name, specialty)
        self.doctors.append(doctor)
        print(f"Doctor '{name}' added successfully.")

    def book_appointment(self, patient_name, doctor_name, date_str):
        date = datetime.strptime(date_str, "%Y-%m-%d").date()
        patient = next((p for p in self.patients if p.name == patient_name), None)
        doctor = next((d for d in self.doctors if d.name == doctor_name), None)

        if not patient:
            print(f"Patient '{patient_name}' not found.")
            return
        if not doctor:
            print(f"Doctor '{doctor_name}' not found.")
            return

        appointment = Appointment(patient, doctor, date)
        self.appointments.append(appointment)
        print(f"Appointment booked for {patient.name} with Dr. {doctor.name} on {date}.")

    def cancel_appointment(self, patient_name, date_str):
        date = datetime.strptime(date_str, "%Y-%m-%d").date()
        for appointment in self.appointments:
            if appointment.patient.name == patient_name and appointment.date == date:
                self.appointments.remove(appointment)
                print(f"Appointment for {patient_name} on {date} cancelled.")
                return
        print(f"No appointment found for {patient_name} on {date}.")

    def view_appointments(self):
        if not self.appointments:
            print("No appointments scheduled.")
        else:
            print("\nScheduled Appointments:")
            for appt in self.appointments:
                print(f"- {appt.date} | {appt.patient.name} with Dr. {appt.doctor.name}")


# Example Usage
if __name__ == "__main__":
    hms = HospitalManagementSystem()

    hms.add_doctor("Ali", "Cardiologist")
    hms.add_doctor("Fatima", "Dermatologist")

    hms.add_patient("Ahmed", 30)
    hms.add_patient("Zara", 25)

    hms.book_appointment("Ahmed", "Ali", "2024-04-10")
    hms.book_appointment("Zara", "Fatima", "2024-04-12")

    hms.view_appointments()

    hms.cancel_appointment("Ahmed", "2024-04-10")
    hms.view_appointments()

