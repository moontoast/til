#TIL how to spin up a flask app in ipython so you can have a shell with app/db context

##This is helpful for playing with different methods or messing around with the ORM

###Here is the python script

```
from main.api_v1 import create_app
from main.services import merchants
from main.models import db

app = create_app()
app.config['SQLALCHEMY_DATABASE_URI'] = '<your local db URI found in the .env file>'
db.init_app(app)

with app.app_context():
    merchant = merchants.get()
    print merchant.name
```

###Run from iPython

```
ipython
%run <path-to-script>
```

I've only tested accessing the orm, but this should work for other operations that require having an app context
