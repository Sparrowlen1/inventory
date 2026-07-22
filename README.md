# Inventory Management System

A Flask-based REST API with a CLI frontend for managing inventory, integrating with OpenFoodFacts for product data.

## Installation

1. Clone the repository: git clone <repo-url>
2. cd projectts

## create virtual enviornment
python -m venv venv
source venv/bin/activate # Windows: venv\Scripts\activate
pip install -r requirements.txt


## Running the API

Start the Flask server:

The API will be available at `http://localhost:5000`.

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET    | /inventory | List all items |
| GET    | /inventory/<id> | Get a single item |
| POST   | /inventory | Add a new item (requires name, price, stock) |
| PATCH  | /inventory/<id> | Update item fields |
| DELETE | /inventory/<id> | Delete an item |
| POST   | /fetch | Fetch product from OpenFoodFacts and add (requires barcode or name, price, stock) |

## CLI Usage

The CLI interacts with the running API. ENSURE THE SERVER IS RUNNING BEFORE USING

## commands
python cli.py list
python cli.py view <id>
python cli.py add <name> <price> <stock> [--brand <brand>] [--ingredients <ingredients>]
python cli.py update <id> [--name <name>] [--brand <brand>] [--ingredients <ingredients>] [--price <price>] [--stock <stock>]
python cli.py delete <id>
python cli.py fetch --barcode <barcode> --price <price> --stock <stock>
python cli.py fetch --name <product_name> --price <price> --stock <stock>

## for testing

## Testing

Run unit tests with pytest:

## External API Integration

The system uses OpenFoodFacts to fetch product details by barcode (exact match) or product name (search). The fetched data is merged with manual price and stock before adding to inventory.

## Notes

- Inventory is stored in memory; restarting the server resets data.
- The CLI uses `requests` to communicate with the API; the server must be running.