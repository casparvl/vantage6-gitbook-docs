---
description: A Python client to interact with the vantage6 server
---

# Python client

It is assumed you installed the [vantage6-client](../../installation/client.md). The Python client aims to completely cover the vantage6-server API functionality.

We only show a few examples here. The methods in the library are all documented in their docstring, you can view them using `help(...)` , e.g. `help(client.user.create)` will show you the parameters needed to create a new user. We also have more extensive tutorials on how to use the clients available on our discourse pages: [https://vantage6.discourse.group/c/tutorials/](https://vantage6.discourse.group/c/tutorials/).

The following code will initialize the Python client and log in to the server.

```python
from vantage6.client import Client

server_url = 'https://where.server.is'
server_port = <port number>
server_api_path = '/path/to/api'
username = 'user'
password = 'password'

client = Client(server_url, server_port, server_api_path, verbose=True)
client.authenticate(username, password)

# this needs to match the collaboration encryption setting. If you do use
# encryption, you specify the private key file path here
client.setup_encryption(None)
```

{% hint style="success" %}
We recommend setting `verbose=True` when initializing the client as this will print much more info.&#x20;
{% endhint %}

The following groups (related to the [concepts](../preliminaries.md#concepts)) of methods are available, most of them have a `list()`, `create()`, `delete()` and `get()` method attached.

* `client.user`
* `client.organization`
* `client.rule`
* `client.role`
* `client.collaboration`
* `client.task`
* `client.result`
* `client.util`
* `client.node`

## Example

```python
help(client.task.create)
#Create a new task
#
#    Parameters
#    ----------
#    collaboration : int
#        Id of the collaboration to which this task belongs
#    organizations : list
#        Organization ids (within the collaboration) which need
#        to execute this task
#    name : str
#        Human readable name
#    image : str
#        Docker image name which contains the algorithm
#    description : str
#        Human readable description
#    input : dict
#        Algorithm input
#    data_format : str, optional
#        IO data format used, by default LEGACY
#    database: str, optional
#        Name of the database to use. This should match the key
#        in the node configuration files. If not specified the
#        default database will be tried.
#
#    Returns
#    -------
#    dict
#        Containing the task information
```
