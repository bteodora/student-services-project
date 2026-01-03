<div align="center">

  <h1>Student Services Management System</h1>
  <h3>Enterprise Academic Administration & Governance Solution</h3>

  <p>
    <img src="https://img.shields.io/badge/Language-C%23_10.0-239120?style=for-the-badge&logo=c-sharp&logoColor=white" alt="C#"/>
    <img src="https://img.shields.io/badge/Framework-.NET_6.0-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET"/>
    <img src="https://img.shields.io/badge/UI_Architecture-WPF_%2F_MVC-blue?style=for-the-badge" alt="WPF MVC"/>
    <img src="https://img.shields.io/badge/Persistence-Custom_Serialization-orange?style=for-the-badge" alt="Serialization"/>
    <img src="https://img.shields.io/badge/Status-Academic_Distinction-success?style=for-the-badge" alt="Status"/>
  </p>

  <p>
    <strong>A robust, monolithic desktop application designed to digitize and automate the complex administrative workflows of higher education institutions.</strong>
  </p>

  <p>
    <a href="OISISI%20Specifikacija%20projekta%202023_2024.pdf"><strong>📄 View Official Specification (PDF) »</strong></a>
    <br />
    <br />
    <a href="#key-features">Key Features</a>
    ·
    <a href="#system-architecture">Architecture</a>
    ·
    <a href="#visual-gallery">Visual Gallery</a>
    ·
    <a href="#installation-and-setup">Installation</a>
  </p>
</div>

---

## 1. Project Overview

**Student Services Management System (SSMS)** is a comprehensive software solution engineered to streamline the data management requirements of university student services. Developed as a capstone project for the **Information Systems and Software Engineering** curriculum at the **Faculty of Technical Sciences (FTN)**, this application serves as a centralized hub for managing the trifecta of academic entities: Students, Faculty, and Curriculum.

The system is designed to simulate a production-ready enterprise environment, addressing the critical need for data consistency, referential integrity, and rigorous access control. By abstracting complex relationships—such as professorial tenure, subject prerequisites, and student grading history—into an intuitive **WPF** interface, the project demonstrates a strict adherence to the **Model-View-Controller (MVC)** architectural pattern.

## 2. Motivation and Background

This project bridges the gap between theoretical software design patterns and practical application development. The primary engineering goal was to build a system that operates without the overhead of a dedicated SQL server, utilizing a custom-built persistence layer while maintaining the robustness of a relational database system.

**Core Design Objectives:**
*   **Architectural Rigor:** Strict separation of concerns between business logic (Model), data presentation (View), and user interaction (Controller).
*   **Data Integrity:** Enforcement of complex constraints (e.g., a Professor cannot be deleted if they are the sole lecturer for an active course).
*   **Algorithmic Complexity:** Implementation of custom sorting algorithms and token-based search parsers.
*   **Accessibility:** Full support for internationalization (I18n) with runtime switching between Serbian and English.

## 3. Key Features

The application is segregated into distinct functional modules, each governed by specific business rules derived from the official specification.

### 3.1. Student Lifecycle Management
*   **Advanced CRUD Operations:** Creation and modification of student records with regex-based validation for Index Numbers (e.g., `RA 12/2021`).
*   **Academic Analytics:**
    *   **Real-time GPA Calculation:** Automatically computes the weighted average of passed exams.
    *   **ECTS Summation:** Aggregates European Credit Transfer System points dynamically.
*   **Curriculum Enrollment:** Logic to handle subject enrollment, ensuring students only enroll in subjects available for their current year of study.
*   **Exam Management:** Records passed exams and includes a strict protocol for **Grade Annulment**, which moves subjects back to the "Unpassed" registry.

### 3.2. Professorial Administration & Governance
*   **Faculty Registry:** detailed profiling including academic title, years of service, and ID card validation.
*   **Departmental Hierarchy:** Organization of faculty into Departments (Katedra).
*   **Head of Department Selection:** The system enforces specific eligibility logic:
    *   Candidate must hold the title of **Full Professor** or **Associate Professor**.
    *   Candidate must possess a minimum of **5 years of tenure**.
*   **Workload Assignment:** Dynamic assignment of professors to subjects with conflict detection.

### 3.3. Subject & Curriculum Management
*   **Course Configuration:** Definition of attributes including Semester (Summer/Winter), ECTS weight, and prerequisites.
*   **Relationship Mapping:** Visualization of all students listening to a specific subject and the assigned teaching staff.
*   **Pagination:** Custom implementation rendering entities in strict pages (e.g., 16 records per view) to optimize UI performance.

### 3.4. Advanced Utilities
*   **Complex Search Engine:** A custom tokenizer implementation allowing multi-term queries (e.g., "Smith John" or "RA 15/2021").
*   **Advanced Sorting:** Multi-attribute sorting (Ascending/Descending) across all data grids.
*   **Localization:** Instant language switching between **Serbian (Latin)** and **English** affecting all labels, tooltips, and dialogs.

## 4. Visual Gallery

The following visuals demonstrate the application's user interface and design consistency.

### Main Dashboard (English Localization)
The central hub providing access to Student, Professor, and Subject entities. Note the custom toolbar and status bar integration.
<div align="center">
  <img src="Screenshots/main_eng.png" alt="Main Window English" width="800" style="border: 1px solid #ddd; border-radius: 4px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>

### Main Dashboard (Serbian Localization)
Demonstration of the localization engine. The UI layout adapts dynamically to text length changes between languages.
<div align="center">
  <img src="Screenshots/main_srb.png" alt="Main Window Serbian" width="800" style="border: 1px solid #ddd; border-radius: 4px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>

### Advanced Entity Analysis
Functionality allowing the set-theoretic comparison of student cohorts across distinct subjects (e.g., "Students who passed Subject A but not Subject B").
<div align="center">
  <img src="Screenshots/comparing.png" alt="Comparing Students" width="800" style="border: 1px solid #ddd; border-radius: 4px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>

### Data Entry & Validation
A standardized modal dialog for editing entities. This form enforces input validation rules before committing data to the model.
<div align="center">
  <img src="Screenshots/edit.png" alt="Edit Professor Window" width="500" style="border: 1px solid #ddd; border-radius: 4px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
</div>

## 5. Architecture and Design

The system is architected to ensure high cohesion and low coupling, utilizing industry-standard design patterns.

### 5.1. Architectural Layers
*   **Model Layer:** Encapsulates the domain entities (`Student`, `Professor`, `Subject`) and business rules. It implements the **Observer Pattern** to notify subscribers of state mutations.
*   **View Layer:** The presentation layer built with **WPF (Windows Presentation Foundation)**. It binds to the controller and reacts to model updates.
*   **Controller Layer:** Orchestrates data flow. It validates user input from the View, invokes Model operations, and determines the appropriate UI response.
*   **Persistence Layer (DAO):** A custom serialization engine (XML/Binary) that persists the object graph to local storage, decoupling the application from specific database technologies.

### 5.2. Design Patterns
*   **Observer:** Facilitates real-time synchronization between the backend data model and the frontend grids.
*   **Singleton:** Manages shared resources such as the Data Store and Localization Context.
*   **Factory Method:** Used for generating entity instances during file deserialization.
*   **DTO (Data Transfer Object):** Flattens complex domain models for specific grid representations.

## 6. Technology Stack

*   **Programming Language:** C# 10.0+
*   **Framework:** .NET 6.0 / .NET Framework 4.8
*   **UI Framework:** Windows Presentation Foundation (WPF)
*   **Serialization:** `System.Runtime.Serialization.Formatters.Binary` / `System.Xml`
*   **IDE:** Microsoft Visual Studio 2022
*   **Version Control:** Git

## 7. Project Structure

The solution is divided into two primary subsystems: **CLI** (for headless operation/testing) and **GUI** (for end-users).

```text
StudentServices/
├── CLI/                    # Command Line Interface Subsystem
│   ├── Console/            # Main Entry Point
│   ├── Controller/         # Logic Handling
│   └── DAO/                # Data Access Implementation
├── GUI/                    # Graphical User Interface Subsystem
│   ├── View/               # XAML Windows and User Controls
│   ├── DTO/                # Data Transfer Objects
│   ├── Localization/       # .resx Resource Dictionaries
│   ├── Assets/             # Icons and Images
│   └── Properties/         # Application Settings
├── Model/                  # Core Domain Entities (Shared)
├── Observer/               # Event Subscription Interfaces
└── Storage/                # Serialization Logic
```

## 8. Installation and Setup

### Prerequisites
*   Windows 10 or Windows 11 Operating System.
*   .NET Desktop Runtime.
*   (Optional) Microsoft Visual Studio 2022 for development.

### Step-by-Step Guide
1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/student-services-management.git
    ```
2.  **Open the Solution:**
    Navigate to the project directory and open `StudentServices.sln` in Visual Studio.
3.  **Restore Dependencies:**
    Run `dotnet restore` or allow Visual Studio to restore NuGet packages.
4.  **Build the Solution:**
    Select the **GUI** project as the Startup Project.
    Press `Ctrl + Shift + B` to build.
5.  **Run:**
    Press `F5` to launch the application.
    *Note: The application includes a pre-seeded dataset in the `bin/Data` directory for demonstration purposes.*

## 9. Testing and Quality Assurance

The stability of the system is ensured through rigorous architectural validation:
*   **Unit Integrity:** Key algorithms (GPA calculation, Search Tokenization) are verified for correctness.
*   **Integration Testing:** The interaction between the Controller and DAO layers is tested to ensure data survives serialization cycles.
*   **Stress Testing:** The GUI is validated against large datasets to ensure the custom pagination and Observer pattern maintain 60fps rendering performance.

## 10. Authors

This project was architected and implemented by:

*   **Teodora Bečejac** (RA 37/2021)
*   **Nataša Radmilović** (RA 20/2021)

*Department of Computing and Control Engineering, Faculty of Technical Sciences.*

## 11. License

This project is distributed for academic and educational purposes. All rights regarding the source code and intellectual property remain with the authors and the Faculty of Technical Sciences.

---

<div align="center">
  <sub>End of Documentation</sub>
</div>
