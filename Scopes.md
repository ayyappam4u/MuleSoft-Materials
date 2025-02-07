_**Scopes:**_

**Async Scope:**
    The Asynchronous Scope in Mule allows you to execute components within the scope asynchronously. 
    When you use the Asynchronous scope, Mule creates a separate thread to handle the execution of the components within that scope,which can run in parallel with other tasks in the flow. 
    The main flow continues executing without waiting for the asynchronous tasks to complete.

**Cache Scope:**
    In MuleSoft, cache scope is a component used to store the result of a process or operation so that subsequent requests can retrieve the data from the cache instead of recomputing or re-fetching it. 
    It helps in improving the performance of APIs and services by reducing unnecessary calls to external systems or performing costly computations.

**Flow Scope:**
    The flow scope is the default scope for a Mule flow, where the main processing occurs. It is used for defining the general sequence of operations, message processing, and routing.

**SubFlow Scope:**
    A sub-flow is a reusable unit of work within a flow. It can be invoked by other flows and sub-flows.

  **For Each:**
    The For Each scope splits a payload into elements and processes them one by one through the components that you place in the scope. 
    It is similar to a for-each/for loop code block in most programming languages and can process any collection, including lists and arrays.

  **Parallel For Each:**
    The Parallel For Each scope enables you to process a collection of messages by splitting the collection into parts that are simultaneously processed in separate routes within the scope of any limitation configured for concurrent-processing. 
    After all messages are processed, the results are aggregated following the same order they were in before the split.

  **Try Scope:**
    The Try scope enables you to handle errors that may occur when attempting to execute any of the components inside the Try scope. 
    It also supports transactions.A Try scope wraps one or more operations, then catches and handles any exceptions that might be thrown by any of these enclosed operations. 
    The behavior is as if you extracted those enclosed event components into a separate flow with its own error handling strategy, but inline, without having to actually define a new flow.

  **Until Successful Scope:**
    The Until Successful scope executes processors within it, in order, until they all succeed or the scope exhausts the maximum number of retries. Until Successful runs synchronously. 
    If any processor within the scope fails to connect or to produce a successful result, Until Successful retries all the processors within it, including the one that failed, until all configured retries are exhausted. 
    If a retry succeeds, the scope proceeds to the next component.If the final retry does not succeed, Until Successful produces an error.

