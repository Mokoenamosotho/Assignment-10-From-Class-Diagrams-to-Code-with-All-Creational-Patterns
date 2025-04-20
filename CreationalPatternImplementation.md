

import os

# Create /creational_patterns directory
creational_dir = "/mnt/data/creational_patterns"
os.makedirs(creational_dir, exist_ok=True)

# Define code for each of the six creational patterns

patterns = {
    "SimpleFactory.cs": """
public abstract class Vehicle {
    public abstract string Drive();
}

public class Car : Vehicle {
    public override string Drive() => "Driving a Car";
}

public class Bike : Vehicle {
    public override string Drive() => "Riding a Bike";
}

public class Truck : Vehicle {
    public override string Drive() => "Driving a Truck";
}

public class VehicleFactory {
    public static Vehicle CreateVehicle(string type) {
        return type switch {
            "Car" => new Car(),
            "Bike" => new Bike(),
            "Truck" => new Truck(),
            _ => throw new ArgumentException("Invalid vehicle type"),
        };
    }
}
""",

    "FactoryMethod.cs": """
public interface IPaymentProcessor {
    string ProcessPayment(double amount);
}

public class CreditCardProcessor : IPaymentProcessor {
    public string ProcessPayment(double amount) => $"Processed {amount} via Credit Card";
}

public class PayPalProcessor : IPaymentProcessor {
    public string ProcessPayment(double amount) => $"Processed {amount} via PayPal";
}

public abstract class PaymentProcessorFactory {
    public abstract IPaymentProcessor CreateProcessor();
}

public class CreditCardProcessorFactory : PaymentProcessorFactory {
    public override IPaymentProcessor CreateProcessor() => new CreditCardProcessor();
}

public class PayPalProcessorFactory : PaymentProcessorFactory {
    public override IPaymentProcessor CreateProcessor() => new PayPalProcessor();
}
""",

    "AbstractFactory.cs": """
public interface IButton {
    string Render();
}

public class WindowsButton : IButton {
    public string Render() => "Rendering Windows Button";
}

public class MacOSButton : IButton {
    public string Render() => "Rendering MacOS Button";
}

public interface IGUIFactory {
    IButton CreateButton();
}

public class WindowsFactory : IGUIFactory {
    public IButton CreateButton() => new WindowsButton();
}

public class MacOSFactory : IGUIFactory {
    public IButton CreateButton() => new MacOSButton();
}
""",

    "Builder.cs": """
public class Pizza {
    public bool Cheese { get; set; }
    public bool Pepperoni { get; set; }
    public bool Mushrooms { get; set; }

    public override string ToString() =>
        $"Pizza with: {(Cheese ? "Cheese, " : "")}{(Pepperoni ? "Pepperoni, " : "")}{(Mushrooms ? "Mushrooms" : "")}";
}

public class PizzaBuilder {
    private readonly Pizza _pizza = new Pizza();

    public PizzaBuilder AddCheese() {
        _pizza.Cheese = true;
        return this;
    }

    public PizzaBuilder AddPepperoni() {
        _pizza.Pepperoni = true;
        return this;
    }

    public PizzaBuilder AddMushrooms() {
        _pizza.Mushrooms = true;
        return this;
    }

    public Pizza Build() => _pizza;
}
""",

    "Prototype.cs": """
public abstract class Shape {
    public string Color { get; set; }
    public abstract Shape Clone();
}

public class Circle : Shape {
    public int Radius { get; set; }
    public override Shape Clone() => (Shape)this.MemberwiseClone();
}

public class Rectangle : Shape {
    public int Width { get; set; }
    public int Height { get; set; }
    public override Shape Clone() => (Shape)this.MemberwiseClone();
}

public class ShapeCache {
    private readonly Dictionary<string, Shape> _cache = new();

    public void LoadCache() {
        _cache["circle"] = new Circle { Color = "Red", Radius = 10 };
        _cache["rectangle"] = new Rectangle { Color = "Blue", Width = 5, Height = 10 };
    }

    public Shape GetShape(string shapeId) => _cache[shapeId].Clone();
}
""",

    "Singleton.cs": """
public class DatabaseConnection {
    private static DatabaseConnection? _instance;
    private static readonly object _lock = new object();

    private DatabaseConnection() { }

    public static DatabaseConnection Instance {
        get {
            lock (_lock) {
                _instance ??= new DatabaseConnection();
                return _instance;
            }
        }
    }

    public string Connect() => "Connected to Database";
}
"""
}

# Write each pattern to its corresponding file
for filename, code in patterns.items():
    with open(os.path.join(creational_dir, filename), "w") as f:
        f.write(code.strip())

creational_dir  # Return path to download

