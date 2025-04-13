# Hospital System
class Patient:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} (Age: {self.age})"


class Doctor:
    def __init__(self, name, specialty):
        self.name = name
        self.specialty = specialty

    def __str__(self):
        return f"Dr. {self.name} ({self.specialty})"


class Appointment:
    def __init__(self, patient, doctor, date):
        self.patient = patient
        self.doctor = doctor
        self.date = date

    def __str__(self):
        return f"{self.date} | {self.patient.name} with {self.doctor.name}"


class HospitalSystem:
    def __init__(self):
        self.patients = []
        self.doctors = []
        self.appointments = []

    def add_patient(self, patient):
        self.patients.append(patient)
        print(f"Patient '{patient.name}' added successfully.")

    def add_doctor(self, doctor):
        self.doctors.append(doctor)
        print(f"Doctor '{doctor.name}' added successfully.")

    def book_appointment(self, patient, doctor, date):
        new_appointment = Appointment(patient, doctor, date)
        self.appointments.append(new_appointment)
        print(f"Appointment booked for {patient.name} with Dr. {doctor.name} on {date}.")

    def cancel_appointment(self, patient_name, date):
        for appointment in self.appointments:
            if appointment.patient.name == patient_name and appointment.date == date:
                self.appointments.remove(appointment)
                print(f"Appointment for {patient_name} on {date} cancelled.")
                return
        print("No matching appointment found.")

    def view_appointments(self):
        if not self.appointments:
            print("No appointments scheduled.")
        else:
            print("\nScheduled Appointments:")
            for app in self.appointments:
                print(f"- {app}")


# Example usage
if __name__ == "__main__":
    hospital = HospitalSystem()

    # Adding doctors
    doc1 = Doctor("Ali", "Cardiologist")
    doc2 = Doctor("Fatima", "Neurologist")
    hospital.add_doctor(doc1)
    hospital.add_doctor(doc2)

    # Adding patients
    pat1 = Patient("Ahmed", 30)
    pat2 = Patient("Zara", 25)
    hospital.add_patient(pat1)
    hospital.add_patient(pat2)

    # Booking appointments
    hospital.book_appointment(pat1, doc1, "2024-04-10")
    hospital.book_appointment(pat2, doc2, "2024-04-12")

    # Viewing all
    hospital.view_appointments()

    # Canceling an appointment
    hospital.cancel_appointment("Ahmed", "2024-04-10")
    hospital.view_appointments()
