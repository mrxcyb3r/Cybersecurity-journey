<div align="center">

# 🐍 Python for Cybersecurity Journey

## 📅 Day 7: Dunder Methods & OOP Project Practice

**📆 Date:** June 30, 2026
**🎯 Focus:** Magic Methods and Applying OOP to a Real Project
**✅ Status:** Completed

*"From OOP theory to building my first real object-oriented project."*

</div>

---

# 📖 Overview

Today wrapped up the core OOP curriculum with **dunder (magic) methods**, then immediately put everything to work by building the beginning of a real **Password Manager** project.

Instead of continuing with isolated OOP exercises, I started applying everything I've learned over the past two days to a practical project. This marks the completion of **Day 7** of my Python for Cybersecurity journey.

---

# 📚 What I Learned

## ✨ Part 1 — Dunder / Magic Methods

"Dunder" = **D**ouble **UNDER**score. Special methods Python calls automatically in certain situations.

### JS Comparison

```javascript
class Money {
    constructor(amount) {
        this.amount = amount;
    }

    toString() {
        return `$${this.amount}`;
    }
}

console.log(`${new Money(50)}`);
````

```python
class Money:
    def __init__(self, amount):
        self.amount = amount

    def __str__(self):
        return f"${self.amount}"

print(Money(50))
```

### Most Useful Dunders

| Dunder     | Triggered by | JS Equivalent     |
| ---------- | ------------ | ----------------- |
| `__init__` | `MyClass()`  | `constructor()`   |
| `__str__`  | `print(obj)` | `toString()`      |
| `__repr__` | debugging    | object inspection |
| `__len__`  | `len(obj)`   | `.length`         |
| `__eq__`   | `==`         | not overridable   |
| `__add__`  | `+`          | not possible      |
| `__lt__`   | `<`          | not possible      |

### Critical Lesson — Never Mutate State Inside `__str__`

```python
# ❌ Wrong
def __str__(self):
    self._password = "*" * len(self._password)
    return self._password

# ✅ Correct
def __str__(self):
    masked = "*" * len(self._password)
    return masked
```

Using a local variable keeps the original password intact.

### Name Mangling

Python internally renames double-underscore attributes:

```python
def __eq__(self, other):
    return self.__amount == other.__amount
```

This allows proper comparisons between instances while preserving encapsulation.

---

## 🛠️ Part 2 — Applied OOP: Password Manager

Started building a real multi-class project to practice object-oriented programming.

### `PasswordEntry`

```python
class PasswordEntry:
    def __init__(self, site, username, password):
        self.site = site
        self.username = username
        self._password = password

    def __str__(self):
        masked = "*" * len(self._password)
        return f"🔑 {self.site} | {self.username} | {masked}"

    def to_dict(self):
        return {
            "site": self.site,
            "username": self.username,
            "password": self._password,
        }

    @staticmethod
    def from_dict(data):
        return PasswordEntry(
            data["site"],
            data["username"],
            data["password"],
        )
```

### Next Features

* PasswordVault class
* JSON save/load
* Password generator
* Password strength checker

---

# 🎯 Skills Gained

By the end of Day 7, I can:

* ✅ Understand and implement Python dunder methods
* ✅ Use `__str__` for readable object output
* ✅ Overload operators with `__eq__`, `__add__`, and `__lt__`
* ✅ Understand Python name mangling
* ✅ Avoid modifying object state inside display methods
* ✅ Use `@staticmethod`
* ✅ Build JSON-ready classes using `to_dict()` and `from_dict()`
* ✅ Apply OOP concepts to a practical Password Manager project
* ✅ Organize code using multiple classes and reusable methods

---

# 📂 Technologies Used

* Python 3
* Object-Oriented Programming (OOP)
* Dunder / Magic Methods
* Operator Overloading
* Name Mangling
* Static Methods
* JSON-ready Data Modeling

---

# 💡 Reflection

> "Today marked the transition from learning object-oriented programming concepts to applying them in a real project. Building the Password Manager helped reinforce classes, encapsulation, static methods, and magic methods while exposing a subtle bug involving `__str__`. Fixing that bug reminded me that display methods should never modify object state. OOP now feels much more natural because I'm using it to build something practical instead of solving isolated exercises."

---

<div align="center">

**Day 7 Complete ✅**

*Python for Cybersecurity — Dunder Methods & Applied OOP* 🐍

</div>

