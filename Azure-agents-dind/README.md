# azure-agent-dind-offline
This is an Azure Agent image that contains a Docker engine inside. Plus it downloads the Azure agent in build time instead of running time.

## Build
```
docker build --build-args AGENT_VERSION=<agent version> -t <image name> .
```

### Example
```
docker build --build-args AGENT_VERSION=2.205.0 -t dockeragent:2.205.0 .
```

### Environment variables
+ AZP_URL: Azure DevOps instance address
+ AZP_TOKEN: PAT token generated from Azure DevOps
+ AZP_AGENT_NAME: Azure DevOps agent name
+ AZP_POOL: Azure DevOps pool name


### Volumes
#### Bind mount
+ Docker daemon configuration
  + `/etc/docker`
+ Docker credentials
  + `/root/.docker/config.json`

#### Named volumes
+ Docker files
  + `/var/lib/docker`

## Run agent 
```
docker run --name <name> -d --network host --privileged <environment variables> <volume mounts> <image name>
```