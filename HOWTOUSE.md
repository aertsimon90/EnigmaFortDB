# EnigmaFortDB User Guide

EnigmaFortDB is a database system designed to securely store your sensitive data. Instead of importing the module, you can copy the content from the "enigmafort.py" file and paste it into your own Python project.

## Copying the Module

Copy all the content from the "enigmafort.py" file and paste it into a file in your own Python project.

## Initialization

```python
# Create a strong password
password = "MyStrongPassword123!"

# Initialize the EnigmaFortDB object
try:
    database = EnigmaFortDB(password)
    print("EnigmaFortDB successfully initialized!")
except RuntimeError as e:
    print("Error:", e)
```

## Adding Data

```python
try:
    database.set("username", "my_username")
    database.set("password", "my_password")
    print("Data added successfully!")
except RuntimeError as e:
    print("Error:", e)
```

## Retrieving Data

```python
username = database.get("username")
password = database.get("password")
print("Username:", username)
print("Password:", password)
```

## Deleting Data

```python
try:
    database.delete("password")
    print("Password deleted successfully!")
except RuntimeError as e:
    print("Error:", e)
```

## Saving and Loading the Database

```python
# Save the database to a file
with open("database.txt", "w") as file:
    file.write(database.download())
    print("Database saved successfully!")

# Load the database from a file
with open("database.txt", "r") as file:
    database.upload(file.read())
    print("Database loaded successfully!")
```

### Note: If you want more fast save and load for your database. use ```database.downloadfast()``` and ```database.uploadfast(base)```
### Note 2: Fast save and load feature, It bypasses base64 encoding, so it creates weaker recording data. But don't worry, this is just an optimized method, it bypasses the precautions of reading data directly, but still all your data is encrypted, so encrypted data cannot be read.

## Password Rules

- Your password must be at least 16 characters long.
- Your password must contain at least 6 different characters.
- Use a strong password with a combination of uppercase letters, lowercase letters, numbers, and special characters.
