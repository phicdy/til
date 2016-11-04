
## JSON API
```python
from flask import Flask
from flask import render_template

app = Flask(__name__)
app.debug = True


@app.route('/api/user', methods=['GET'])
def user():
    return UserAPI.handle()
```

```python
from flask import jsonify

def handle():
	data = {
		'name': 'Tanaka TaroA',
		'age': 18
	}
	response = jsonify(data)
	response.status_code = 200
	return response
```
