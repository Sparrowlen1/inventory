# Inventory Management System

A **Flask-based REST API** with a **CLI frontend** for managing inventory. The system integrates with **OpenFoodFacts** to fetch product information by barcode or product name.

---

# Installation

## 1. Clone the Repository

```bash
git clone <repo-url>
cd projectts
```

## 2. Create and Activate a Virtual Environment

### Linux/macOS

```bash
python -m venv venv
source venv/bin/activate
```

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

# Running the API

Start the Flask server:

```bash
python app.py
```

The API will be available at:

```
http://localhost:5000
```

---

# API Endpoints

|   Method   | Endpoint          | Description                                                                                |
| :--------: | ----------------- | ------------------------------------------------------------------------------------------ |
|   **GET**  | `/inventory`      | Retrieve all inventory items                                                               |
|   **GET**  | `/inventory/<id>` | Retrieve a single inventory item                                                           |
|  **POST**  | `/inventory`      | Add a new item (requires `name`, `price`, and `stock`)                                     |
|  **PATCH** | `/inventory/<id>` | Update one or more fields of an item                                                       |
| **DELETE** | `/inventory/<id>` | Delete an inventory item                                                                   |
|  **POST**  | `/fetch`          | Fetch a product from OpenFoodFacts using a barcode or product name and add it to inventory |

---

# CLI Usage

The CLI communicates with the running API.

> **ENSURE THE SERVER IS RUNNING BEFORE USING THE CLI, AND RUN THE COMMANDS ON ANOTHER TERMINAL AFTER RUNNING python app.py.**

## Available Commands

### List all inventory items

```bash
python cli.py list
```

### View a single item

```bash
python cli.py view <id>
```

### Add a new item

```bash
python cli.py add <name> <price> <stock> [--brand <brand>] [--ingredients <ingredients>]
```

### Update an existing item

```bash
python cli.py update <id> [--name <name>] [--brand <brand>] [--ingredients <ingredients>] [--price <price>] [--stock <stock>]
```

### Delete an item

```bash
python cli.py delete <id>
```

### Fetch a product by barcode

```bash
python cli.py fetch --barcode <barcode> --price <price> --stock <stock>
```

### Fetch a product by name

```bash
python cli.py fetch --name <product_name> --price <price> --stock <stock>
```

---

# Testing

Run the unit tests using **pytest**:

```bash
pytest
```

---

# External API Integration

The application integrates with **OpenFoodFacts** to retrieve product information.

Supported lookup methods include:

* Barcode (exact match)
* Product name (search)

The fetched product details are combined with the manually supplied **price** and **stock** before being added to the inventory.

---

# Notes

* Inventory data is stored **in memory**. Restarting the server will reset all inventory data.
* The CLI uses the **requests** library to communicate with the Flask API.
* The Flask server **must be running** before executing any CLI commands.
