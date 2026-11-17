# Blood Donation Management System (BDMS)

**Course:** Object-Oriented Programming (OOP) – 2nd Year Project  
**Project Team:** Navya Gupta and Samhita Jain  
**Language:** Python 3 (Tkinter GUI)

**GitHub Repository:** [Blood Donation Management System](https://github.com/11navyagupta/blood-donation-management-system)

---

## Original Project Attribution

This repository is based on an existing Blood Donation Management System project. Original source: [uniqueaccount-eng/blood-donation-management-system](https://github.com/uniqueaccount-eng/blood-donation-management-system).

---



## Project Structure

```text
blood-donation-management-system/
│
├── main.py                     # Entry point to run the application
├── README.md                   # Project documentation
├── requirements.txt            # Dependencies list (uses standard library)
├── .gitignore                  # Git ignore file
│
├── models/                     # OOP Classes
│   ├── __init__.py
│   ├── enums.py                # Blood groups, urgency, and status enums
│   ├── person.py               # Person (base class), Donor, Recipient, Staff
│   ├── blood_unit.py           # BloodUnit class with expiry calculation
│   └── request.py              # BloodRequest and DonationRecord classes
│
├── services/                   # Business logic and algorithms
│   ├── __init__.py
│   ├── compatibility.py        # ABO/Rh compatibility rules (Strategy pattern)
│   ├── inventory_manager.py    # Inventory tracking & FIFO dispatch (Singleton)
│   ├── donor_service.py        # Donor registration and eligibility logic
│   └── request_service.py      # Request handling and matching logic
│
├── storage/                    # Data storage
│   ├── __init__.py
│   ├── storage_interface.py    # Abstract storage interface
│   └── json_storage.py         # JSON file storage with default sample data
│
├── ui/                         # Tkinter GUI
│   ├── __init__.py
│   ├── theme.py                # Colors, fonts, and ttk styles
│   ├── app.py                  # Main GUI window with tab navigation
│   ├── dashboard_view.py       # Dashboard tab (summary cards, stock bars)
│   ├── donor_view.py           # Donors tab (donor list, search, registration)
│   ├── inventory_view.py       # Inventory tab (stock table, expiry warnings)
│   ├── request_view.py         # Requests tab (hospital requests, matching)
│   └── analytics_view.py       # SDG 3 & project info tab
│
├── tests/                      # Unit testing
│   ├── __init__.py
│   └── test_oop_system.py      # Unit tests for OOP classes and logic
│
├── docs/                       # Project documentation
│   ├── project_synopsis.md     # Project synopsis report
│   ├── sdg_mapping.md          # SDG mapping writeup
│   └── uml_diagrams.md         # Class and sequence diagrams
│
└── data/                       # JSON files where data is saved
    ├── donors.json
    ├── inventory.json
    ├── requests.json
    └── donations.json
```

---

## How to Run the Project

### Requirements
* Python 3.8 or higher.
* No extra `pip install` required — the project runs entirely on Python's built-in libraries (`tkinter`, `json`, `datetime`, `unittest`).

### Running the App
1. Open terminal or Command Prompt in the project folder:
   ```bash
   cd blood-donation-management-system
   ```
2. Run the main file:
   ```bash
   python main.py
   ```

### Running Unit Tests
To verify all classes and logic:
```bash
python -m unittest tests/test_oop_system.py
```

---

## Features

* **Dashboard:** Shows total units in stock, registered donors, pending requests, and blood units expiring within 7 days.
* **Donor Management:** Add new donors with instant eligibility check (age 18-65, weight >= 50kg, and 90-day cooldown). Search and filter by name or blood group.
* **Inventory Tracking:** View all blood units with color-coded expiry warnings. Discard expired units.
* **Emergency Requisitions:** Hospitals can request blood by urgency level (Routine, Urgent, Critical). Click "Match & Fulfill" to automatically find compatible units.
* **FIFO Blood Allocation:** Units with the closest expiry date are allocated first to prevent wastage.
* **Data Persistence:** Automatically saves all donors, units, and requests into clean JSON files in the `data/` folder.
