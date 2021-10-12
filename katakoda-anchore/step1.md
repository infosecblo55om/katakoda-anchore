# Setting up Anchore.

Anchore: https://github.com/anchore/anchore-engine/

* Result/Analysis of a docker image can take some time to update as anchore-engine saves the analysis in a database for audit and future purposes.
<br/>

## How to install

* Let's do the prerequisite first.

`python3.7 -m pip install --upgrade testresources`{{execute}}

`python3.7 -m pip install setuptools`{{execute}}

* Start the Anchore-engine and database using docker containers.

`mkdir anchore && cd anchore`{{execute}}

`curl https://engine.anchore.io/docs/quickstart/docker-compose.yaml > docker-compose.yaml`{{execute}}

`docker-compose up -d`{{execute}}

`docker ps`{{execute}}

Here, you will see that the docker container for anchore-engine(api, analyzer, policy-engine etc.) and database are now running successfully.

* Install the anchore cli using pip.

`python3.7 -m pip install anchorecli`{{execute}}

`anchore-cli --version`{{execute}}

<br/>