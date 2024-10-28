# root-of-the-equationdef newton_raphson(f, f_prime, initial_guess, tolerance=1e-6, max_iterations=1000):
    """
    Find a root of the equation f(x) = 0 using the Newton-Raphson method.

    Parameters:
    - f (function): The function for which we want to find the root.
    - f_prime (function): The derivative of the function f.
    - initial_guess (float): Initial guess for the root.
    - tolerance (float): The precision tolerance (default is 1e-6).
    - max_iterations (int): Maximum number of iterations to perform (default is 1000).

    Returns:
    - float: The root of the equation if found within tolerance; otherwise, None.
    """
    x = initial_guess
    for i in range(max_iterations):
        fx = f(x)
        fx_prime = f_prime(x)
        
        if abs(fx) < tolerance:
            print(f"Root found after {i+1} iterations")
            return x
        
        if fx_prime == 0:
            raise ValueError("Derivative is zero. No solution found.")
        
        x = x - fx / fx_prime  # Newton-Raphson iteration
        
    print("Exceeded maximum iterations. No solution found.")
    return None

# Example function and its derivative
# Function: f(x) = x^2 - 2 (Finding the square root of 2)
def f(x):
    return x**2 - 2

def f_prime(x):
    return 2 * x

# Example usage:
initial_guess = 1.0
root = newton_raphson(f, f_prime, initial_guess)

if root is not None:
    print(f"The root is approximately: {root}")
else:
    print("Root not found within tolerance.")
