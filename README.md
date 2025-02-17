# React useEffect Return Statement Without Cleanup

This repository demonstrates a common, yet subtle, bug in React's `useEffect` hook: using the return statement without providing a cleanup function. This can lead to unexpected behavior and potential memory leaks.  The bug and its solution are explained below.

## Bug
The bug is demonstrated in `bug.js`.  A `useEffect` hook attempts to log a message once upon component mount. However, it includes a `return;` statement which is functionally equivalent to `return ()=>{};`, and thus does not perform any cleanup. While seemingly harmless here, this can cause problems with effects that need to clean up after themselves (e.g., subscriptions, timers, event listeners).

## Solution
The corrected code is in `bugSolution.js`. The `return` statement is removed, ensuring no unnecessary return is executed, and the effect will execute correctly.

## How to reproduce
Clone the repository and run:
```bash
npm install
npm start
```