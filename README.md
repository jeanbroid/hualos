# Hualos - Keras Total Visualization project

For now, this is a simple demo where a Flask server exposes an API to publish and consume events in the form of JSON objects. The Hualos callback `RemoteMonitor` can publish events to the server, and the Hualos landing page listens to the server and displays incoming data on a c3.js graph.


## Installation

* `git clone https://github.com/gabrieldemarmiesse/hualos`
* `pip install hualos`


## Usage:

* start the server: `hualos-serve`
* open the landing page: `http://localhost:9000/`
* launch a Keras experiment with the `RemoteMonitor` callback:

```python
from hualos.HualosCallback import RemoteMonitor
remote = RemoteMonitor(root='http://localhost:9000')

model.fit(X_train, Y_train, batch_size=batch_size, nb_epoch=nb_epoch, validation_data=(X_test, Y_test), callbacks=[remote])
```

* the available metrics of the experiment will start being graphed in real time on the landing page.


## Help

* `hualos-serve --help`


## Dependencies:

- Python:
    - Flask
    - gevent

- JS (included in the repo):
    - d3.js
    - c3.js
