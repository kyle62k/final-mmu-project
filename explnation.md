class MemoryManager:
    """
    Memory Manager Class

    Attributes:
        memory_size (int): Total size of the memory to be managed.
        memory (list): Represents the memory itself.
        page_table (dict): Page table to map virtual addresses to physical addresses.
    """

    def __init__(self, memory_size):
        """
        Initialization method for MemoryManager class.

        Args:
            memory_size (int): Total size of the memory.
        """
        self.memory_size = memory_size
        self.memory = [0] * memory_size
        self.page_table = {}  # Page table to map virtual addresses to physical addresses

    def allocate_memory(self, process_id, num_pages):
        """
        Allocate memory for a process.

        Args:
            process_id (int): Identifier for the process.
            num_pages (int): Number of pages required by the process.

        Returns:
            list: List of allocated pages if successful, None otherwise.
        """
        # Simulate memory allocation for a process
        if process_id in self.page_table:
            print(f"Process with ID {process_id} already allocated memory.")
            return

        required_memory = num_pages * self.memory_size // 10  # Each page takes 10% of total memory
        if required_memory > self.memory_size:
            print("Error: Insufficient memory!")
            return

        allocated_pages = []
        for i in range(num_pages):
            allocated_pages.append(len(self.page_table) + i)
            self.page_table[process_id + i] = len(self.page_table) + i

        print(f"Allocated {required_memory} units of memory to process {process_id}.")
        return allocated_pages

    def access_memory(self, process_id, virtual_address):
        """
        Access memory for a process using its virtual address.

        Args:
            process_id (int): Identifier for the process.
            virtual_address (int): Virtual address of the memory to access.

        Returns:
            int: Physical address if successful, None otherwise.
        """
        if process_id not in self.page_table:
            print(f"Error: Process with ID {process_id} does not have memory allocated.")
            return None

        if virtual_address not in range(self.memory_size):
            print("Error: Invalid virtual address!")
            return None

        physical_address = self.page_table[process_id] * (self.memory_size // 10) + virtual_address
        return physical_address

    def deallocate_memory(self, process_id):
        """
        Deallocate memory for a process.

        Args:
            process_id (int): Identifier for the process.
        """
        if process_id not in self.page_table:
            print(f"Error: Process with ID {process_id} does not have memory allocated.")
            return

        del self.page_table[process_id]
        print(f"Memory for process {process_id} deallocated.")

# Example usage
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
