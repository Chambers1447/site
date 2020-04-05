# Function to catch exceptions in Python

```python
def catch(function):
    def wrapper(*args):
        try:
            return function(*args)
        except Exception as error:
            return {'error': error}
    return wrapper
```