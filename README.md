# Flight Route Optimisation System

[cite_start]This project simulates a flight planning system that helps users find optimal flight itineraries based on various criteria. [cite_start]It can minimize the number of flights, reduce costs, or balance both factors, considering real-world constraints such as connection times.

### Features

* [cite_start]**Minimize Flights & Earliest Arrival:** Find a route with the fewest flights, prioritizing the earliest arrival time if multiple options have the same number of flights.
* [cite_start]**Cheapest Trip:** Identify the route with the lowest total fare, irrespective of the number of flights involved.
* [cite_start]**Minimize Flights & Cheapest:** Discover a route with the minimum number of flights, selecting the cheapest option among routes with the same number of flights.
* [cite_start]**Realistic Constraints:** Accounts for a 20-minute minimum layover time between connecting flights.

### Project Structure

* [cite_start]`flight.py`: Defines the `Flight` class, representing individual flight details such as flight number, departure/arrival cities and times, and fare.
* [cite_start]`planner.py`: Contains the `Planner` class, which implements the core logic for finding optimal flight routes based on the specified objectives. It uses a custom `Heap` implementation for efficient route searching.
* `main.py`: A script for reading flight data from a file, initializing the `Planner`, and running tests for different optimization goals.

### Getting Started

#### Prerequisites

* Python 3.x

#### Installation

1.  **Clone the repository:**

    ```bash
    git clone [https://github.com/YOUR_USERNAME/Flight-Planner.git](https://github.com/YOUR_USERNAME/Flight-Planner.git)
    cd Flight-Planner
    ```

#### Usage

To run the flight planner, you will need an input file specifying the flight details. The format of the input file is as follows:
&lt;start_city> &lt;end_city>
&lt;n> &lt;m>
&lt;u1> &lt;v1> &lt;start_time1> &lt;end_time1> &lt;cost1>
&lt;u2> &lt;v2> &lt;start_time2> &lt;end_time2> &lt;cost2>
...
&lt;um> &lt;vm> &lt;start_timem> &lt;end_timem> &lt;costm>

### Development

#### `Flight` Class

The `Flight` class in `flight.py` has the following attributes:

* `flight_no` (int): Unique identifier for the flight. 
* `start_city` (int): The starting city number. 
* `departure_time` (int): The departure time in minutes. 
* `end_city` (int): The destination city number. 
* `arrival_time` (int): The arrival time in minutes. 
* `fare` (int): The cost of the flight. 

#### `Planner` Class

The `Planner` class in `planner.py` includes the following methods: 

* `__init__(self, flights)`: Initializes the planner with a list of `Flight` objects.  This method has a time complexity of <span class="math-inline">O\(m\)</span>. 
* `least_flights_earliest_route(self, start_city, end_city, t1, t2)`: Returns a route satisfying optimization goal 1.  The departure time must be <span class="math-inline">\\ge t1</span> and arrival time <span class="math-inline">\\le t2</span>.  This method should run in <span class="math-inline">O\(m\)</span> time. 
* `cheapest_route(self, start_city, end_city, t1, t2)`: Returns a route satisfying optimization goal 2.  The departure time must be <span class="math-inline">\\ge t1</span> and arrival time <span class="math-inline">\\le t2</span>.  This method should run in <span class="math-inline">O\(m \\log m\)</span> time. 
* `least_flights_cheapest_route(self, start_city, end_city, t1, t2)`: Returns a route satisfying optimization goal 3.  The departure time must be <span class="math-inline">\\ge t1</span> and arrival time <span class="math-inline">\\le t2</span>.  This method should run in <span class="math-inline">O\(m \\log m\)</span> time. 

**Note on Time Complexity:** `m` refers to the total number of flights, and `n` refers to the number of cities. It's noted that <span class="math-inline">n</span> is <span class="math-inline">O\(m\)</span>. 
