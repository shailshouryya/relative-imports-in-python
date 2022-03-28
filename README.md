# Overview

The `alpha` package mirrors the example given in https://stackoverflow.com/a/62191010 from [Attempted relative import with no known parent package](https://stackoverflow.com/questions/55084977/attempted-relative-import-with-no-known-parent-package/62191010#comment126613974_62191010)

Package structure:
```
/alpha
    __init__.py
    /beta
        __init__.py
        /delta
            __init__.py
            script.py
    /gamma
        __init__.py
        e1.py
        /epsilon
            __init__.py
            script.py
    /zeta
        __init__.py
        script.py
```
- If you have a module in `delta` called `script.py`
  - alpha > beta > delta > script.py
  - and want to call the `e1` module
    - alpha > gamma > e1.py
  - you can import the `e1` module into the `script` module inside `delta` using
    - `from ...gamma import e1`
  - NOTE that if you want to run this as a script, the following will NOT work:
    - `python -m alpha/beta/delta/script.py`
  - If you want to run this as a script, you need to call this using:
    - `python -m alpha.beta.delta.script`
