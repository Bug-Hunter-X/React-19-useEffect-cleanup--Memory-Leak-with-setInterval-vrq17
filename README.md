# React 19 useEffect Cleanup: Memory Leak Example

This repository demonstrates a common mistake in React 19's `useEffect` hook that can cause memory leaks. The example shows how forgetting to return a cleanup function from `useEffect` when using `setInterval` can lead to memory leaks.

## Bug

The `bug.js` file contains the buggy code. The `setInterval` is started in the `useEffect` hook, but there's no cleanup function to stop it when the component unmounts. This leads to the `setInterval` continuing to run even after the component is no longer needed.

## Solution

The `bugSolution.js` file provides the corrected code.  A cleanup function is returned from `useEffect`, which uses `clearInterval` to stop the interval when the component unmounts.  This prevents memory leaks.

## How to reproduce

1. Clone this repository.
2. Navigate to the repository directory in your terminal.
3. Run `npm install` to install dependencies.
4. Run `npm start` to start the development server.

Observe the count increasing. Even if you navigate away from the page or refresh it, the count will likely continue to increment in the console. This demonstrates the memory leak.
The fixed version will stop incrementing when the component unmounts. 