- **Type:** #[[__ 📦 Projects]] [[📋 Outline]]
- **Summary:** How to manage settings in a large Django codebase
- **Related Notes and Sources:**
    - 
- **Notes:**
    - **Environment Variable or Default**
        - `os.environ.get("DB_NAME", "local_db")`
        - For a simple app with only two environments, you can use the fact that `os.environ.get` takes a default value if the environment variable isn't present
        - This works well for simple apps with only a local and a production environment and if there are only a few variables
    - **Environment Variable and Conditional**
        - Use an environment variable for the environment (`dev`, `prod`, etc) and import additional settings based on 
        - Works great when you have multiple environments, but not many environment variables that are different between the two
        - Can use it in hybrid with the previous approach and only the settings that are unique to one environment need to be part of the two
    - **WordPress Approach**
        - One big conditional for everything
        - Test the environment and duplicate the variable declarations over and over again in each layer of the conditional


```python
if ENV == "PRODUCTION":
  # bunch of stuff
elif ENV == "TESTING":
  # bunch of stuff
else:
  # bunch of stuff```
    - **Settings Module**
        - Create a folder called `settings/` with an `__init__.py` in it and dynamically set and retrieve variables
        - This is good for more complex applications
```

