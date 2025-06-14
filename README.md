# timeout: Python Function Timeout Decorator

**Introduction**

`timeout` is a Python library that provides an easy-to-use `@timeout()` decorator to add timeout limits to any Python function. If the function does not complete execution within the specified time, it will be forcibly terminated and a `TimeoutError` exception will be raised. The library leverages the `multiprocessing` module to safely terminate timed-out functions without blocking the main process.

**Features**

*   **Easy to Use:** Simply use a decorator to implement the timeout functionality.
*   **Non-Blocking:** Utilizes the `multiprocessing` module to avoid blocking the main process.
*   **Exception Handling:** Captures exceptions in the child process and re-raises them.
*   **Flexible Configuration:** The timeout duration is passed as an argument when calling the function, eliminating the need to modify the function definition.

**Installation**

1.  **Clone the project from GitHub:**

    ```bash
    git clone https://github.com/ivsoan/timeout.git
    ```

2.  **Navigate to the `timeout-0.0.1` directory:**

    ```bash
    cd ./timeout/timeout-0.0.1
    ```

3.  **Install using `pip`:**

    ```bash
    pip install .
    ```

    This will install the `timeout-0.0.1` library and its dependencies.

**Usage**

1.  **Import the `timeout` decorator:**

    ```python
    from timeout import timeout
    ```

2.  **Decorate your function with `@timeout()`:**

    ```python
    import time
    from timeout import timeout

    @timeout()  # Note: Parentheses are required
    def my_function(duration, **kwargs):
        """
        A function that simulates a time-consuming operation.
        """
        time.sleep(duration)
        return f"Function completed, took {duration} seconds"
    ```

3.  **Call the decorated function, specifying the `timeout` parameter (in seconds):**

    ```python
    try:
        result = my_function(duration=5, timeout=2)  # Set timeout to 2 seconds
        print(result)
    except TimeoutError as e:
        print(f"Timeout occurred: {e}")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")
    ```

    **Note:** The `timeout` parameter must be specified when calling the function and passed as a keyword argument (`kwargs`). If the `timeout` parameter is not specified, a `ValueError` will be raised.
