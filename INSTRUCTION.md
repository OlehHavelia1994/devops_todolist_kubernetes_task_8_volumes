## Instructions for Validation
### 1. Prepare the Environment

Before running any kubectl commands, ensure you are in the .infrastructure directory where the configuration files are located:

`cd .infrastructure`

### 2. Validate if the App is Running
To verify that the application has been deployed successfully and the pod is active, run:

`kubectl get pods -n todoapp`

Expected Outcome: You should see a pod named todoapp-xxxxx with the status Running and 1/1 in the READY column.

### 3. Validate ConfigMap Data Mounting
ConfigMap data is mounted in the /app/config directory. To verify that the files are present and mounted in the correct structure, execute:

`kubectl exec -n todoapp deployment/todoapp -- ls -la /app/config`

Expected Outcome: The output should list the files defined in your configMap.yml.

### 4. Validate Secret Data Mounting
To verify the secret data mounted in the /app/secret directory:

`kubectl exec -n todoapp deployment/todoapp -- ls /app/secret`

### 5. Validate Persistent Volume (Data Folder)
To ensure the storage directory /app/data is present inside the container:

`kubectl exec -n todoapp deployment/todoapp -- ls -d /app/data`

Expected Outcome: The output should simply be /app/data. This confirms the directory is mounted and accessible.