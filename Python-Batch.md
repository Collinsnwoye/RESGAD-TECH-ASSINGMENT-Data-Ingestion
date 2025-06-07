# Batch Processing using Python!
This example demonstrates a basic ETL (Extract, Transform, Load) process using batch ingestion in Python.
It generates random sample data, processes it in chunks (batches), applies a simple transformation to each record, and loads the results into a Pandas DataFrame for display.

![image](https://github.com/user-attachments/assets/abf8f61f-beca-4662-8d8f-a4f0ea093cae)

### Below is a high-level overview of the key functions used in this ETL pipeline:

- **`generate_mock_data(num_records)`**  
  Creates a list of mock records, each with a random `id` and `value`. This simulates incoming raw data.

- **`process_in_batches(data, batch_size)`**  
  Splits the full dataset into smaller chunks (batches) of size `batch_size` using a generator.

- **`transform_data(batch)`**  
  Transforms each record in a batch by adding a new field `transformed_value` (`value × 1.1`).

- **`load_data(batch)`**  
  Simulates loading the transformed records into a database by printing them to the console.

- **`main()`**  
  Orchestrates the ETL flow: generates data, processes it in batches, transforms each batch, and "loads" it.


```python
import random
import uuid

def generate_sample_data():
  data = []
  for i in range(100):
    record = {
        "id": str(uuid.uuid4()),
        "value": random.random()            
    }
    data.append(record)
  return data
```

#### Understanding the Sample Data Generator Function
When building a function to generate sample data, it’s important to consider structure, flexibility, and practical processing needs. Here's a breakdown of the design choices we made:

**1. Define the Data Structure**
We represent each individual data record as a dictionary in Python.
**Why a dictionary?**

- A dictionary allows us to store key-value pairs, making the data self-describing like column name and value in tabular formats.
- Each field (e.g., 'id', 'value') has a label (the key), which makes the data easier to work with when analyzing, transforming, or loading it into other systems.

**2. Determine the Number of Records**
The function accepts a num_records parameter so the number of records is flexible. This allows you to generate as little or as much data as needed (within reason).

To prevent performance issues, we include a limit of 200 records. This ensures the function remains lightweight and manageable.

**3. Use a Container to Hold Records**
We use a list to collect all generated records.
**Why a list?**

- A list is ideal for holding an ordered sequence of items — in this case, dictionaries.
- It allows easy iteration over the records, which is essential for batch processing.
- Lists support standard Python operations for slicing, batching, and indexing — useful when you want to process data in chunks (e.g., 50 records at a time).

 **4. Loop to Populate the Container**
A for loop runs num_records times, generating a new dictionary during each iteration. This record is then appended to the list, building our dataset step-by-step.

**5. Function Purpose: Simulating a Lightweight Data Source**
Think of this function as a sample database. It simulates structured data that you can use for: Testing transformation logic; Experimenting with batch processing; Practicing data loading techniques.