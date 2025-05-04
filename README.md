## Bakery Management Simulation

This project simulates the daily operations of a bakery using multi-processing and IPC techniques in C. It models various bakery roles (chefs, bakers, sellers, supply-chain employees, and customers) coordinating via shared memory and semaphores.

### Features

* **Multi-process Architecture**: Separate processes for each role (chefs, bakers, sellers, supply-chain, customers).
* **IPC via Shared Memory**: Fast exchange of counters, orders, and inventory data.
* **Synchronization**: Binary semaphores protect shared resources and enforce ordering.
* **Configurable Parameters**: Customize number of workers, order probabilities, inventory sizes, and simulation duration.
* **Graceful Shutdown**: Capture signals to clean up shared memory segments and semaphores.

### Prerequisites

* GCC (with support for `-pthread`)
* POSIX IPC libraries (`sys/ipc.h`, `sys/shm.h`, `sys/sem.h`)
* Make

### Installation & Build

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/bakery-simulation.git
   cd bakery-simulation
   ```

2. **Compile**

   ```bash
   make all
   ```

3. **Clean build artifacts**

   ```bash
   make clean
   ```

### Configuration

Edit `config.h` to adjust:

* `CHEF_COUNT`, `BAKER_COUNT`, `SELLER_COUNT`, `SUPPLY_CHAIN_COUNT`, `CUSTOMER_COUNT`
* `OVEN_CAPACITY`, `WAREHOUSE_CAPACITY`
* Probabilities: `arrival_prob`, `want_prob[]`
* Simulation runtime (`MAX_TIME_SECONDS`)

### Running the Simulation

```bash
./bakery_simulation
```

During the run, statistics are logged to `stats.log` and the GUI module (if enabled) displays real-time status.

### Project Structure

```
├── header.h            # all headers
├── manager.c           # Entry point: sets up IPC, forks processes
├── chef.c              # Chef process logic
├── baker.c             # Baker process logic
├── seller.c            # Seller process logic
├── customer.c          # Customer process logic
├── supplier.c          # Supply-chain process logic
├── ipc_utils.c         # Helpers: create/attach shared memory and semaphores
├── ipc_utils.h         # Haders for ipc_utilis.c
├── bakery_gui.c        # OpenGL GUI display
├── config.c            # loads configuration
├── configuration       # Bakery Configuration
├── config.h            # Header for config.c
├── struct.h            # Shared data structures
├── Makefile            # Build commands
└── README.md           # Project documentation
```

### Contributing

1. Fork the repo
2. Create a feature branch (`git checkout -b feature-name`)
3. Commit your changes (`git commit -m "Add feature"`)
4. Push to the branch (`git push origin feature-name`)
5. Open a pull request

### License

Distributed under the MIT License. See `LICENSE` for details.

### Author

Taleen Abuzulof — Computer Engineering, Birzeit University

---

Enjoy simulating your bakery! Feel free to open issues for bugs or feature requests.
