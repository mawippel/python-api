# Python API

## Infrastructure

You'll need a storage account with a blob container, and a Service Bus with a queue.

```
az storage account create -n MyStorageAccountName -g MyResourceGroupName
az servicebus namespace create -n MyServiceBusName -g MyResourceGroupName
```

## Development

Prepare the environment:

```shell
# Update packages
sudo apt-get update

# Install latest Python
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.7 python3.7-dev python3.7-venv

# Install latest pip
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
sudo python3.7 get-pip.py

# Check if pip is matching for Python 3.7
pip --version
```

Install dependencies:

```shell
python3.7 -m venv env
. env/bin/activate
pip install --upgrade pip
pip install pylint
pip install -r requirements.txt
pip install azure-storage-blob --pre
```

Create the configurations file:

```
config.ini
```

Generate sample data:

```
python3.7 data_generator.py
```

Run it:

```
python3.7 main.py
```

With Docker:

```
docker build -t python-api .
docker run -it --rm --name python-api python-api
```

## References

[Azure Storage Blobs client library for Python](https://github.com/Azure/azure-sdk-for-python/tree/master/sdk/storage/azure-storage-blob)

[How to use Service Bus queues with Python](https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-python-how-to-use-queues)

[Installing PIP](https://pip.pypa.io/en/stable/installing/)
