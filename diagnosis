import random

class Patient:
    def __init__(self, name, symptoms):
        self.name = name
        self.symptoms = symptoms

    def __str__(self):
        return f"Patient Name: {self.name}\nSymptoms: {', '.join(self.symptoms)}"

def show_symptoms():
    symptoms_list = [
        "fever", "cough", "sneezing", "runny nose", "headache", "nausea",
        "vomiting", "body ache", "fatigue", "sore throat", "chills",
        "shortness of breath", "diarrhea", "stomach pain", "dizziness",
        "itchy eyes", "rash", "loss of taste", "loss of smell", "sweating",
        "earache", "swelling", "joint pain", "blurred vision", "chest pain"
    ]
    print("Available Symptoms:")
    for i, symptom in enumerate(symptoms_list, 1):
        print(f"{i}. {symptom}")
    return symptoms_list

def diagnose(patient, possible_diagnoses):
    diagnoses = {}
    for condition, required_symptoms in possible_diagnoses.items():
        matched_symptoms = set(patient.symptoms).intersection(required_symptoms)
        confidence = (len(matched_symptoms) / len(required_symptoms)) * 100
        if confidence > 0:
            diagnoses[condition] = confidence

    return diagnoses

if __name__ == "__main__":
    print("Enter patient details:")
    name = input("Patient Name: ")

    symptoms_list = show_symptoms()
    while True:
        print("\nSelect symptoms by entering numbers separated by commas (e.g., 1, 3, 5):")
        selected_input = input()
        try:
            selected_indices = [int(index.strip()) - 1 for index in selected_input.split(",")]
            symptoms = [symptoms_list[i] for i in selected_indices if 0 <= i < len(symptoms_list)]
            if symptoms:
                break
            else:
                print("No valid symptoms selected. Please try again.")
        except ValueError:
            print("Invalid input. Please enter numbers only.")

    patient = Patient(name, symptoms)

    possible_diagnoses = {
        "Flu": {"fever", "cough", "body ache", "chills"},
        "Common Cold": {"sneezing", "runny nose", "cough", "sore throat"},
        "Allergies": {"sneezing", "itchy eyes", "rash", "swelling"},
        "Food Poisoning": {"nausea", "vomiting", "stomach pain", "diarrhea"},
        "Migraine": {"headache", "nausea", "dizziness"},
        "Viral Infection": {"fever", "sneezing", "fatigue"},
        "Bronchitis": {"cough", "shortness of breath", "chest pain"},
        "Asthma": {"shortness of breath", "chest pain"},
        "COVID-19": {"fever", "cough", "loss of taste", "loss of smell"},
        "Dengue": {"fever", "body ache", "rash", "fatigue"}
    }

    diagnoses = diagnose(patient, possible_diagnoses)
    print("\n" + str(patient))

    if diagnoses:
        print("Diagnosis and Confidence Levels:")
        for condition, confidence in diagnoses.items():
            print(f"- {condition}: {confidence:.2f}%")
        if max(diagnoses.values()) > 50:
            print("\n Confidence exceeds 50%. It is recommended to visit a doctor.")
    else:
        print("Diagnosis: Unable to determine. Consult a doctor or provide more specific symptoms.")

