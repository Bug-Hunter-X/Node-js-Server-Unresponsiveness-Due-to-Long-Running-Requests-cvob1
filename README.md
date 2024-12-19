# Node.js Server Unresponsiveness

This repository demonstrates a common issue in Node.js servers: unresponsiveness due to long-running requests.  The server uses a simple `http.createServer` to handle requests.  A simulated long-running task blocks the event loop, preventing the server from responding to new requests.

## Problem

The provided `server.js` creates a server that simulates a long-running task (a 5-second delay).  During this time, the server becomes unresponsive.  New requests will hang until the long-running task completes.

## Solution

The `serverSolution.js` file demonstrates the solution by using asynchronous operations. Node.js is single-threaded and event driven. When a long task is performed synchronously on the main thread, it blocks the main thread and also the event loop from executing other tasks and thus blocking requests.

The solution is to handle the long-running tasks asynchronously by using workers or threads to offload tasks to separate threads to free the main thread and the event loop.