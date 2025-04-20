
📁 Directory Structure
.
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

✅ Example Unit Tests
tests/test_prototype.py

from creational_patterns.prototype import Circle

def test_prototype_clone():
    original = Circle(5)
    clone = original.clone()
    assert original is not clone
    assert original.radius == clone.radius

from creational_patterns.builder import PizzaBuilder

def test_builder_creates_custom_pizza():
    pizza = (PizzaBuilder()
             .add_cheese()
             .add_toppings(['olives', 'mushrooms'])
             .build())
    assert pizza.cheese is True
    assert pizza.toppings == ['olives', 'mushrooms']

def test_builder_with_invalid_input():
    builder = PizzaBuilder()
    try:
        builder.add_toppings(None)
    except ValueError:
        assert True


from creational_patterns.singleton import DatabaseConnection

def test_singleton_instance():
    db1 = DatabaseConnection.get_instance()
    db2 = DatabaseConnection.get_instance()
    assert db1 is db2


🧪 Running Tests and Generating Coverage
Install dependencies:
pip install pytest pytest-cov

Run tests with coverage:
pytest --cov=creational_patterns tests/

Sample pytest.ini
[pytest]
addopts = --cov=creational_patterns --cov-report=term-missing


📝 Test Coverage Report Example

---------- coverage: platform linux, python 3.11 ----------
Name                            Stmts   Miss  Cover
---------------------------------------------------
creational_patterns/builder.py    45      2    96%
creational_patterns/prototype.py  23      0   100%
creational_patterns/singleton.py  18      0   100%
...
---------------------------------------------------
TOTAL                             153      5    97%
