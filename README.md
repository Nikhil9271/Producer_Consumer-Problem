# Producer_Consumer-Problem
Producer-Consumer Simulation Using Semaphores
This repository contains a web-based implementation of the Producer-Consumer problem using semaphores for synchronization, built with HTML, CSS, and JavaScript. The Producer-Consumer problem is a classic synchronization challenge where producers add items to a shared buffer, and consumers remove items, with semaphores ensuring thread-safe operations to prevent buffer overflow or underflow. This implementation visualizes the process in a browser, showing the buffer state and logging actions in real-time.

Table of Contents

.Overview
.Features
.Prerequisites
.Installation
.Usage
.Implementation Details
.Example Output

Overview
The Producer-Consumer problem models a scenario where:

Producers generate items (sequential IDs) and add them to a fixed-size buffer.
Consumers remove items from the buffer for processing.
A shared buffer has a limited capacity, and synchronization is required to:
Prevent producers from adding items to a full buffer.
Prevent consumers from removing items from an empty buffer.
Ensure thread-safe access to the buffer.



This implementation uses JavaScript's asynchronous programming with Promises to simulate semaphores (mutex, full, empty) in a single-threaded environment, mimicking multithreaded behavior. The simulation runs in a web browser, displaying the buffer state visually and logging producer/consumer actions.
Features

Interactive web interface with a graphical buffer display.
Real-time logging of producer and consumer actions.
Semaphore-based synchronization using mutex (mutual exclusion), full (filled slots), and empty (empty slots).
Configurable buffer size and maximum items (set to 5 and 20 by default).
Start and stop controls to manage the simulation.
Responsive design with animated buffer slots and a modern UI.

Prerequisites
To run this project, you need:

A modern web browser (e.g., Chrome, Firefox, Edge).
No additional software or dependencies, as the application runs entirely in the browser.

Installation

Clone the Repository:
git clone https://github.com/your-username/producer-consumer-semaphores.git
cd producer-consumer-semaphores


Open the Application:

Open index.html in a web browser (e.g., double-click the file or serve it via a local server).
No build or compilation is required, as the application uses vanilla HTML, CSS, and JavaScript.


Optional: Serve Locally:

To avoid CORS issues or test on a local server, use a simple HTTP server:python -m http.server 8000


Then, access the application at http://localhost:8000.



Usage

Open the Application:

Load index.html in your browser to see the simulation interface.


Start the Simulation:

Click the Start button to begin the producer-consumer simulation.
The producer generates items (IDs from 0 to 19) and adds them to the buffer.
The consumer removes items from the buffer.
The buffer display updates in real-time, with filled slots highlighted in red.
Actions are logged in the console below the buffer.


Stop the Simulation:

Click the Stop button to halt the simulation at any time.
The log will indicate when the simulation stops.


Configure the Simulation:

Modify BUFFER_SIZE (default: 5) and MAX_ITEMS (default: 20) in the JavaScript code to change the buffer capacity or number of items produced.
Adjust the sleep delays (Math.random() * 1000) to control the speed of producer/consumer actions.



Implementation Details
The implementation includes:

HTML/CSS:
A responsive UI with a buffer display (slots), status bar, start/stop buttons, and a log console.
CSS uses gradients, animations, and a modern design for visual appeal.


JavaScript:
Buffer: A fixed-size array (size 5 by default) to store items.
Semaphores:
mutex: Ensures exclusive access to the buffer using a lock and queue.
empty: Tracks available buffer slots (initialized to BUFFER_SIZE).
full: Tracks filled buffer slots (initialized to 0).


Producer: Waits on empty, acquires mutex, adds an item, updates indices, and signals full.
Consumer: Waits on full, acquires mutex, removes an item, updates indices, and signals empty.
Asynchronous Execution: Uses async/await and Promises to simulate concurrent producer/consumer behavior.
Visualization: Updates the buffer display and logs actions after each operation.


Simulation Control:
The startSimulation function initializes the buffer and semaphores, running producer and consumer concurrently.
The stopSimulation function halts execution and clears semaphore queues.



The code is modular and can be extended to add multiple producers/consumers or different item types.
Example Output
The log console might display:
Simulation started.
Produced item 0. Buffer: [0]
Full = 1, Empty = 4
------------------------------------------------
Consumed item: 0. Buffer: []
Full = 0, Empty = 5
------------------------------------------------
Produced item 1. Buffer: [1]
Full = 1, Empty = 4
------------------------------------------------
...
Simulation completed.
