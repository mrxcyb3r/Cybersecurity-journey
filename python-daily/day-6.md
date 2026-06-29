<div align="center">

# 🐍 Python for Cybersecurity Journey

## 📅 Day 6: Object-Oriented Programming (OOP)

**📆 Date:** June 29, 2026
**🎯 Focus:** Classes, Objects, Inheritance, Encapsulation & Static Methods
**✅ Status:** Completed

*"Thinking like a JS dev, writing like a Pythonista."*

</div>

---

# 📖 Overview

Today I learned Python Object-Oriented Programming from scratch — and because I come from a frontend JavaScript background, everything mapped almost 1:1 to what I already knew. Classes, inheritance, private fields, getters/setters, and static methods all exist in both languages. Python just has different syntax and a few unique quirks.

This marks the completion of **Day 6** of my Python for Cybersecurity journey.

---

# 📚 What I Learned

## 🧱 1. Classes, Objects & `__init__`

A **class** is a blueprint. An **object** is an instance built from that blueprint. `__init__` is the constructor that runs automatically when an object is created.

### JS vs Python — Side by Side

| Concept | JavaScript | Python |
|---|---|---|
| Blueprint | `class Dog { }` | `class Dog:` |
| Constructor | `constructor()` | `__init__(self)` |
| Instance property | `this.name = name` | `self.name = name` |
| Method | `bark() { }` | `def bark(self):` |
| Create instance | `new Dog("Rex")` | `Dog("Rex")` ← no `new`! |

### Key Syntax

```python
class Dog:
    def __init__(self, name, breed, age):
        self.name = name      # this.name → self.name
        self.breed = breed
        self.age = age

    def bark(self):
        print(f"{self.name} says: Woof!")   # backticks → f-strings

dog1 = Dog("Rex", "Labrador", 3)            # no `new` keyword
dog1.bark()  # Rex says: Woof!
```

### Key Rules
- `self` is always the first parameter of every method (like `this` in JS)
- `__init__` runs automatically when the object is created
- Default parameter values work just like JS: `def __init__(self, likes=0):`

---

## 🧬 2. Inheritance

Inherit from a parent class to reuse and extend its behaviour — exactly like `extends` in JS.

### JS vs Python

| | JavaScript | Python |
|---|---|---|
| Inherit syntax | `class Dog extends Animal` | `class Dog(Animal):` |
| Call parent constructor | `super(name)` | `super().__init__(name)` |
| `super` itself | `super` | `super()` ← needs `()` |

### Key Syntax

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print(f"{self.name} makes a sound.")


class Dog(Animal):                     # extends Animal
    def __init__(self, name, breed):
        super().__init__(name)         # call parent constructor
        self.breed = breed

    def speak(self):                   # override parent method
        print(f"{self.name} barks!")


dog = Dog("Rex", "Labrador")
dog.speak()   # Rex barks!
```

### Key Rules
- Parent class goes in parentheses: `class Child(Parent):`
- Always call `super().__init__(...)` to set up parent's attributes
- Overriding a method works the same as JS — just redefine it in the child class

---

## 🔒 3. Encapsulation & `@property`

Control access to class data using private attributes and getters/setters.

### Privacy Levels

| | JavaScript | Python |
|---|---|---|
| Public | `field` | `field` |
| Convention only | — | `_field` (single underscore) |
| Name-mangled | `#field` | `__field` (double underscore) |

> Python doesn't truly block access like JS — it uses naming conventions and trusts developers to respect them. Single `_` is the most common real-world pattern.

### `@property` — Python's Getter/Setter

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius        # private-ish attribute

    @property
    def radius(self):                # getter — accessed like a property, not method
        return self._radius

    @radius.setter
    def radius(self, value):         # setter — validates before setting
        if value < 0:
            raise ValueError("Radius can't be negative!")
        self._radius = value

c = Circle(5)
print(c.radius)   # 5  ← no () needed!
c.radius = 10     # calls setter
c.radius = -1     # ❌ ValueError!
```

### Key Rules
- Use `self.email = email` in `__init__` (not `self._email`) so the setter validates on creation too
- A `@property` getter must `return` the value — no side effects
- `raise ValueError("msg")` is Python's `throw new Error("msg")`
- `"@" not in value` is Python's `!value.includes("@")`

---

## ⚡ 4. Static Methods

A static method belongs to the **class itself**, not any instance. No `self` — it's a pure utility function that lives inside a class as a namespace.

### JS vs Python

```javascript
// JavaScript
class Validator {
    static isValidEmail(email) {
        return email.includes("@");
    }
}
Validator.isValidEmail("a@b.com");
```

```python
# Python
class Validator:
    @staticmethod
    def is_valid_email(email):      # no self!
        return "@" in email

Validator.is_valid_email("a@b.com")
```

### Real World Analogy

`Math.max()`, `Math.floor()`, `Math.random()` in JS — you never write `new Math()`. Static methods work the same way: just a toolbox of utilities hanging off a class.

### 3 Types of Methods

```python
class MyClass:
    def instance_method(self):    # needs an object (self)
        pass

    @classmethod
    def class_method(cls):        # gets the class itself (no JS equivalent)
        pass

    @staticmethod
    def static_method():          # no self, no cls — pure utility
        pass
```

### Key Rules
- No `self` parameter — ever
- Call on the class directly: `FormValidator.is_valid_email(email)`
- Never call on a variable: `email.is_valid_email(email)` ← ❌ wrong!

---

# 🛠️ Practices Completed

## 📝 Practice 1 — `BlogPost` Class

> Modelled a reusable Card component as a Python object

```python
class BlogPost:
    def __init__(self, title, author, likes=0):
        self.title = title
        self.author = author
        self.likes = likes          # default like useState(0)

    def like(self):
        self.likes += 1             # like clicking a Like button

    def render(self):
        print(f"📝 {self.title} by {self.author} | 👍 {self.likes} likes")

post1 = BlogPost("My First Post", "Alice")
post1.render()   # 📝 My First Post by Alice | 👍 0 likes
post1.like()
post1.like()
post1.render()   # 📝 My First Post by Alice | 👍 2 likes
```

---

## 🖱️ Practice 2 — `UIComponent` + `Button` Inheritance

> Modelled a component hierarchy like React's class components

```python
class UIComponent:
    def __init__(self, tag, text):
        self.tag = tag
        self.text = text

    def render(self):
        print(f"tag: {self.tag} | text: {self.text}")


class Button(UIComponent):
    def __init__(self, text, color):
        super().__init__("button", text)   # hardcode tag, pass text up
        self.color = color

    def render(self):
        print(f"tag: {self.tag} | text: {self.text} | color: {self.color}")

    def click(self):
        print(f"🖱️ Button '{self.text}' was clicked!")

base = UIComponent("div", "Hello")
btn = Button("Click me", "blue")

base.render()   # tag: div | text: Hello
btn.render()    # tag: button | text: Click me | color: blue
btn.click()     # 🖱️ Button 'Click me' was clicked!
```

---

## 👤 Practice 3 — `UserProfile` with Encapsulation

> Private attributes + getter/setter validation

```python
class UserProfile:
    def __init__(self, username, email):
        self._username = username
        self.email = email              # triggers setter on creation!

    @property
    def email(self):
        return self._email

    @email.setter
    def email(self, value):
        if "@" not in value:
            raise ValueError("Invalid email!")
        self._email = value

    def display(self):
        print(f"👤 {self._username} | ✉️ {self._email}")

user = UserProfile("alice", "alice@example.com")
user.display()              # 👤 alice | ✉️ alice@example.com
user.email = "new@test.com"
user.email = "notanemail"   # ❌ ValueError: Invalid email!
```

---

## ✅ Practice 4 — `FormValidator` Static Methods

> A utility class — never instantiated, just a toolbox

```python
class FormValidator:

    @staticmethod
    def is_valid_email(email):
        if "@" not in email or "." not in email:
            print("❌ email invalid")
        else:
            print("✅ email OK")

    @staticmethod
    def is_valid_username(name):
        if 3 <= len(name) <= 20:
            print("✅ username OK")
        else:
            print("❌ username invalid")

    @staticmethod
    def is_strong_password(pwd):
        if len(pwd) >= 8 and any(c.isdigit() for c in pwd):
            print("✅ password OK")
        else:
            print("❌ password weak")

    @staticmethod
    def validate_form(email, username, password):
        FormValidator.is_valid_email(email)
        FormValidator.is_valid_username(username)
        FormValidator.is_strong_password(password)

FormValidator.validate_form("alice@example.com", "alice123", "pass1234")
# ✅ email OK
# ✅ username OK
# ✅ password OK
```

---

# 🎯 Skills Gained

By the end of Day 6, I can:

- ✅ Define classes with `__init__` and instance methods
- ✅ Use `self` correctly (equivalent of `this` in JS)
- ✅ Set default parameter values in constructors
- ✅ Create child classes with `class Child(Parent):`
- ✅ Call parent constructors with `super().__init__()`
- ✅ Override methods in subclasses
- ✅ Use `_private` naming convention for encapsulation
- ✅ Create getters and setters with `@property`
- ✅ Validate data and `raise` errors
- ✅ Write `@staticmethod` utility methods
- ✅ Call static methods on the class, not on instances

---

# 📂 Technologies Used

- Python 3
- OOP (Classes, Inheritance, Encapsulation, Static Methods)
- `@property` decorator
- f-strings
- `any()` + generator expressions

---

# 💡 Reflection

> "Coming from JavaScript, Python OOP felt immediately familiar. `__init__` is just `constructor`, `self` is just `this`, and `class Dog(Animal)` is just `class Dog extends Animal`. The biggest mindset shift was `@property` for getters/setters and remembering that `super()` needs parentheses. Most importantly — no `new` keyword when creating objects!"

---

<div align="center">

*Day 6 / Python for Cybersecurity — OOP Foundations Complete* 🐍

</div>
