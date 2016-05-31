# python-metmet
Python universal method/function metadata decorator.

# Example usage
```python
from metmet import MetaCollector

# collect methods with their metatdata
class WebApi:
    handlers = MetaCollector()
    def __init__(self):
        self.handlers = self.handlers.bind(self)

    @handlers('/')
    def handle_index(self):
        return 'Index page'

    @handlers('/login', method='POST')
    @handlers('/logout', method='POST')
    def handle_login_logout(self):
        return 'Not implemented'


api = WebApi()
# use collected items (register in webserver, etc)
for handler in api.handlers:
    print(handler.args)
    print(handler.kwargs)
    print(handler.method())
```
