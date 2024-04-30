# MMU Simulator

This repository contains a basic Memory Management Unit (MMU) simulator implemented in Python.

## Introduction

The MMU simulator provides a simplified environment for understanding memory management concepts, including memory allocation, access, and deallocation.

## How to Run

To run the MMU simulator, follow these steps:

1. **Install Python:**
   Ensure that you have Python installed on your system. You can download Python from the official website: [Python.org](https://www.python.org/).

2. **Clone the Repository:**
   Clone this repository to your local machine using Git:
   git clone [https://github.com/kyle62k/final-mmu-project.git]
3. **Navigate to the Directory:**
Use the `cd` command to navigate into the project directory:
cd final-mmu-project

4. **Run the Simulator:**
Execute the Python script `main.py` using the Python interpreter:

python main.py


5. **Test the Code:**
After running the script, observe the output to see memory allocation, access, and deallocation processes. You can modify the example usage part of the script to test different scenarios.

## Example Usage

```python
# Example usage of MemoryManager class
if __name__ == "__main__":
 mmu = MemoryManager(memory_size=100)

 # Allocate memory for process 1
 pages_allocated = mmu.allocate_memory(process_id=1, num_pages=2)

 # Access memory for process 1
 if pages_allocated:
     for page in pages_allocated:
         for i in range(10):
             virtual_address = page * 10 + i
             physical_address = mmu.access_memory(process_id=1, virtual_address=virtual_address)
             print(f"Virtual Address: {virtual_address} -> Physical Address: {physical_address}")

 # Deallocate memory for process 1
 mmu.deallocate_memory(process_id=1)

