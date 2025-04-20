# Assignment-10-From-Class-Diagrams-to-Code-with-All-Creational-Patterns



/src
  ├── User.cs
  ├── Database.cs
  ├── Backup.cs
  ├── Recovery.cs
  ├── AIModel.cs
  ├── AuditLog.cs
  └── ComplianceReport.cs
  
  ├── creational_patterns/
│   ├── simple_factory.py
│   ├── factory_method.py
│   ├── abstract_factory.py
│   ├── builder.py
│   ├── prototype.py
│   ├── singleton.py
│   └── README.md
├── tests/
│   ├── test_simple_factory.py
│   ├── test_factory_method.py
│   ├── test_abstract_factory.py
│   ├── test_builder.py
│   ├── test_prototype.py
│   ├── test_singleton.py
├── requirements.txt
└── pytest.ini

readme_content = """
# 🏥 Hospital Database Management System - C# Implementation

This project provides a foundational set of C# classes for a hospital database management system with built-in backup, recovery, AI anomaly detection, monitoring, and compliance reporting.

## 📁 Folder Structure


# Creational Design Patterns

This directory contains implementations of all six major creational design patterns, each demonstrating a specific use case relevant to real-world software development.

---

## 1. Simple Factory 🏭

**Use Case**: Centralized object creation for multiple related types.

**Implementation**: `VehicleFactory` returns instances of `Car`, `Bike`, or `Truck` based on input.

**Justification**: Used Simple Factory to decouple object instantiation from client code and enable easy extension for new vehicle types.

---

## 2. Factory Method 🧱

**Use Case**: Delegate instantiation responsibility to subclasses.

**Implementation**: `PaymentProcessor` interface with concrete implementations: `CreditCardProcessor` and `PayPalProcessor`.

**Justification**: Used Factory Method to allow different payment strategies without modifying core payment logic, promoting open/closed principle.

---

## 3. Abstract Factory 🏗️

**Use Case**: Creating families of related objects without specifying concrete classes.

**Implementation**: `GUIFactory` returns UI elements like `WindowsButton` or `MacOSButton`.

**Justification**: Used Abstract Factory to ensure consistency among UI components (e.g., all MacOS widgets or all Windows widgets).

---

## 4. Builder 🍕

**Use Case**: Construct complex objects with many optional parameters.

**Implementation**: `PizzaBuilder` allows step-by-step construction with methods like `.addCheese()` and `.addToppings()`.

**Justification**: Used Builder for Pizza class due to many optional ingredients and the need for flexible, readable construction syntax.

---

## 5. Prototype 🧬

**Use Case**: Clone existing complex objects rather than creating from scratch.

**Implementation**: `ShapeCache` stores and returns clones of `Circle` and `Rectangle` prototypes.

**Justification**: Used Prototype to avoid expensive setup cost when creating multiple similar objects (e.g., shapes with default styles or metadata).

---

## 6. Singleton 🔒

**Use Case**: Ensure a class has only one instance and provide a global point of access.

**Implementation**: `DatabaseConnection` class restricts instantiation and ensures a single shared connection.

**Justification**: Used Singleton for database connection management to maintain one active connection across the app and prevent resource leaks.

---

## ✅ How to Run

Each file contains a `main()` method demonstrating usage. Run them independently to see each pattern in action.

```bash
python simple_factory.py


