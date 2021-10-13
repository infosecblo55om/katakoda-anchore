## How to scan Docker images

* Check the status, if all the services are up.

`anchore-cli --url http://localhost:8228/v1 --u admin --p foobar system status`{{execute}}

* Export the environment variable. Credentials can be passed through cli.

`export ANCHORE_CLI_URL=http://localhost:8228/v1 && export ANCHORE_CLI_USER=admin && export ANCHORE_CLI_PASS=foobar`{{execute}}

* Analyze the image. Anchore first fetches the added docker image and then performs the analysis. Here, we are adding two images for the scan: openjdk and debian.

`anchore-cli image add openjdk:8-jre-alpine`{{execute}}

`anchore-cli image add docker.io/library/debian:latest`{{execute}}

* Check the status of the analysis. When both the analysis are finished, move to next step.

`anchore-cli image list`{{execute}}

Check the status again by running the above command if both the images are not analysed.

* Check for the result. You will have three flags to check the result: os, non-os, all. Here, we are considering *all*

`anchore-cli image vuln openjdk:8-jre-alpine all`{{execute}}

`anchore-cli image vuln docker.io/library/debian:latest all`{{execute}}

* If the result is not published, wait for the database sync and then check the result again. Check if the result is updated to the database.

`anchore-cli system feeds list`{{execute}}

If pending is showing, wait for 5-10mins and check the results again.
