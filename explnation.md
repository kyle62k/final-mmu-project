class MemoryManager:
    def __init__(self, memory_size):
        self.memory_size = memory_size
        self.memory = [0] * memory_size
        self.page_table = {}

# MemoryManager Class Initialization:
# MemoryManager is a class responsible for managing memory.
# __init__ method initializes the MemoryManager object with a specified memory_size.
# It initializes two main attributes:
# - memory: A list representing the memory with each element initialized to 0.
# - page_table: A dictionary to map process IDs to their respective physical memory locations.

def allocate_memory(self, process_id, num_pages):
    # Simulate memory allocation for a process
    if process_id in self.page_table:
        print(f"Process with ID {process_id} already allocated memory.")
        return

    required_memory = num_pages * self.memory_size // 10
    if required_memory > self.memory_size:
        print("Error: Insufficient memory!")
        return

    allocated_pages = []
    for i in range(num_pages):
        allocated_pages.append(len(self.page_table) + i)
        self.page_table[process_id + i] = len(self.page_table) + i

    print(f"Allocated {required_memory} units of memory to process {process_id}.")
    return allocated_pages

# Memory Allocation Method:
# allocate_memory method allocates memory for a process with a given process_id and num_pages.
# It checks if the process already has memory allocated. If so, it prints an error message and returns.
# It calculates the required memory for the process based on the number of pages.
# It checks if the required memory exceeds the total memory available. If so, it prints an error message and returns.
# It allocates memory for the process by updating the page table and returns the allocated pages.

def access_memory(self, process_id, virtual_address):
    if process_id not in self.page_table:
        print(f"Error: Process with ID {process_id} does not have memory allocated.")
        return None

    if virtual_address not in range(self.memory_size):
        print("Error: Invalid virtual address!")
        return None

    physical_address = self.page_table[process_id] * (self.memory_size // 10) + virtual_address
    return physical_address

# Memory Access Method:
# access_memory method accesses memory for a process with a given process_id and virtual_address.
# It checks if the process has memory allocated. If not, it prints an error message and returns None.
# It checks if the virtual address is within the valid range. If not, it prints an error message and returns None.
# It calculates the physical address based on the page table and returns it.

def deallocate_memory(self, process_id):
    if process_id not in self.page_table:
        print(f"Error: Process with ID {process_id} does not have memory allocated.")
        return

    del self.page_table[process_id]
    print(f"Memory for process {process_id} deallocated.")

# Memory Deallocation Method:
# deallocate_memory method deallocates memory for a process with a given process_id.
# It checks if the process has memory allocated. If not, it prints an error message and returns.
# It removes the process from the page table to deallocate memory and prints a message confirming deallocation.
