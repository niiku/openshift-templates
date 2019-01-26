# Sonatype Nexus on OpenShift

Original from https://github.com/OpenShiftDemos/nexus

```
post:
  execNewPod:
    containerName: ${SERVICE_NAME}
    command:
      - "/bin/bash"
      - "-c"
      - "curl -o /tmp/nexus-functions -s https://raw.githubusercontent.com/niiku/openshift-templates/master/nexus/scripts/nexus-functions; source /tmp/nexus-functions; add_nexus3_redhat_repos ${NEXUS_ADMIN_USERNAME} ${NEXUS_ADMIN_PASSWORD} http://${SERVICE_NAME}:8081"
```

# Import Templates

Sonatype Nexus 3:
```
oc create -f https://raw.githubusercontent.com/niiku/openshift-templates/master/nexus/nexus3-persistent-template.yaml
```

# Deploy Nexus 3
```
oc new-app nexus3-persistent
```

# Deploy Specific Version
```
oc new-app nexus3-persistent -p NEXUS_VERSION=3.15.1
```
