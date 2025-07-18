# EtherealTrades: A Synthetic Order Book and Market Simulation Engine

EtherealTrades is a Python-based platform designed for simulating financial markets, primarily focusing on the generation of synthetic order book data and market behavior. It provides a flexible and configurable environment for researchers, algorithmic traders, and developers to prototype and test trading strategies, analyze market dynamics, and generate realistic data for machine learning applications without the need for real-time market connections or live trading. It's built for scenarios requiring controlled and reproducible market conditions, offering a sophisticated alternative to simple random data generation.

The primary purpose of EtherealTrades is to provide a granular, customizable market simulation environment. It achieves this by allowing users to define various market parameters, including the types of participants, their trading strategies, order book depth, volatility levels, and event-driven scenarios. The engine generates a stream of synthetic order book updates, trades, and market data, providing a rich dataset for analysis and backtesting. Users can define custom order types and market impact models to simulate realistic trading conditions. This allows for rigorous testing of algorithms under specific and repeatable market scenarios, crucial for assessing the robustness and profitability of trading strategies.

EtherealTrades stands apart by offering a detailed control over market dynamics. Instead of relying on historical data or live market feeds, the engine empowers users to create markets tailored to their specific needs. This is particularly valuable for testing algorithms in edge cases, simulating rare events, and exploring the impact of different market microstructure parameters. The modular design allows for easy extension and customization, enabling users to integrate their own trading logic, market models, and data analysis tools. Furthermore, the engine provides a standardized API for interacting with the simulated market, facilitating the development and integration of external trading systems.

This repository provides the core engine for market simulation, along with example scripts and configurations to get started quickly. The engine is designed to be scalable and efficient, allowing for the simulation of high-frequency trading scenarios with minimal computational overhead. The emphasis is on providing a powerful, flexible, and reproducible environment for market research and algorithmic trading development.

## Key Features

*   **Customizable Order Book:** Define the initial state of the order book, including bid and ask prices, quantities, and liquidity levels. The engine supports various order types, including limit orders, market orders, and stop-loss orders.
*   **Agent-Based Modeling:** Simulate the behavior of different market participants (e.g., informed traders, noise traders, market makers) with configurable trading strategies and risk profiles. Agents can be programmed to react to market events and execute orders based on predefined rules.
*   **Event-Driven Simulation:** Introduce external events (e.g., news announcements, regulatory changes) that can impact market prices and trading activity. Events can be triggered at specific times or based on market conditions.
*   **Market Impact Modeling:** Implement models to simulate the impact of large trades on market prices. The engine supports various impact functions, allowing users to model the price elasticity of demand and supply.
*   **Data Export and Analysis:** Export the generated market data in various formats (e.g., CSV, JSON) for further analysis and visualization. The engine also provides built-in tools for calculating key market statistics, such as volatility, volume, and order book depth.
*   **Modular Architecture:** The engine is designed with a modular architecture, allowing users to easily extend and customize the functionality. New agents, order types, market models, and data analysis tools can be added without modifying the core engine.
*   **Reproducible Simulations:** Ensure reproducibility by seeding the random number generators used in the simulation. This allows users to run the same simulation multiple times and obtain the same results.

## Technology Stack

*   **Python:** The primary programming language used for the engine. Python provides a rich ecosystem of libraries for scientific computing, data analysis, and visualization.
*   **NumPy:** A fundamental library for numerical computing in Python. NumPy provides efficient array operations and mathematical functions.
*   **Pandas:** A powerful library for data analysis and manipulation. Pandas provides data structures for representing and manipulating tabular data.
*   **SciPy:** A library for scientific computing in Python. SciPy provides algorithms for optimization, integration, interpolation, and signal processing.
*   **Random:** Used to generate random numbers, central to the simulation of agent behavior and order generation.

## Installation

1.  Clone the repository:

    git clone https://github.com/ezozu/EtherealTrades.git

2.  Navigate to the project directory:

    cd EtherealTrades

3.  Create a virtual environment:

    python3 -m venv venv

4.  Activate the virtual environment:

    source venv/bin/activate  (Linux/macOS)

    venv\Scripts\activate (Windows)

5.  Install the required dependencies:

    pip install -r requirements.txt

## Configuration

The engine can be configured using environment variables and configuration files.

*   **Environment Variables:**

    *   `ETHEREALTRADES_LOG_LEVEL`: Sets the logging level (e.g., DEBUG, INFO, WARNING, ERROR).
    *   `ETHEREALTRADES_DATA_DIR`: Specifies the directory for storing generated market data.

*   **Configuration Files:**

    The engine uses YAML configuration files to define the parameters of the simulation. Example configuration files are provided in the `config` directory. Edit these files to customize the market parameters, agent strategies, and event schedules. A typical config file might contain the initial order book state, and agent behavioral characteristics.

## Usage

To run a simulation, use the `run_simulation.py` script:

python run_simulation.py --config config/example_config.yaml

This will execute the simulation based on the parameters defined in the specified configuration file. The generated market data will be stored in the directory specified by the `ETHEREALTRADES_DATA_DIR` environment variable.

Example code to create a basic order book:

class OrderBook:
    def __init__(self):
        self.bids = []
        self.asks = []
    def add_bid(self, price, quantity):
        self.bids.append((price, quantity))
        self.bids.sort(reverse=True)
    def add_ask(self, price, quantity):
        self.asks.append((price, quantity))
        self.asks.sort()

## Contributing

We welcome contributions to EtherealTrades! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure all tests pass before submitting the pull request. Add tests if necessary.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/ezozu/EtherealTrades/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to thank the open-source community for providing the tools and libraries that make this project possible.