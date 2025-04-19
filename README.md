# Class for Participant
class Participant:
    def __init__(self, name):
        self.name = name

# Class for Organizer
class Organizer:
    def __init__(self, name):
        self.name = name

    def create_event(self, name, date):
        return Event(name, date, self)

# Class for Schedule
class Schedule:
    def __init__(self, time, venue):
        self.time = time
        self.venue = venue

# Class for Event
class Event:
    def __init__(self, name, date, organizer):
        self.name = name
        self.date = date
        self.organizer = organizer
        self.participants = []
        self.schedule = None

    def add_participant(self, participant):
        self.participants.append(participant)

    def set_schedule(self, schedule):
        self.schedule = schedule

    def show_details(self):
        print(f"Event: {self.name}")
        print(f"Date: {self.date}")
        print(f"Organizer: {self.organizer.name}")
        if self.schedule:
            print(f"Time: {self.schedule.time}, Venue: {self.schedule.venue}")
        print("Participants:")
        for p in self.participants:
            print(f"- {p.name}")

# Main Program
org = Organizer("Prof. Sharma")
event = org.create_event("College Tech Fest", "2025-04-15")

# Adding schedule
schedule = Schedule("10:00 AM", "Auditorium")
event.set_schedule(schedule)

# Registering participants
event.add_participant(Participant("Anjali"))
event.add_participant(Participant("Ravi"))

# Show all event details
event.show_details()
