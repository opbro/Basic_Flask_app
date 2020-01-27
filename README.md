# Basic_Flask_app

```
import logging
from flask import Flask, request, jsonify

app = Flask(__name__)


@app.route("/")
def index():
    app.logger.info(vars(request))
    return jsonify("Example Flask App")

@app.route("/tasking", methods=["GET"])
def tasking():
    d = dict()
    for key, value in request.args.items():
        app.logger.info("{}, {}".format(key, value))
        d[key] = value
    return jsonify(d)


if __name__ == "__main__":
    import os
    ip = os.environ.get('LISTEN_HOST', '0.0.0.0')
    port = os.environ.get('LISTEN_PORT', 8200)
    debug = os.environ.get('DEBUG', True)
    app.run(host=ip, port=port, debug=debug)
```
