# Exposing Gen AI Agents via Oracle Digital Assistant

## Retrieve the Agent Endpoint ID

1. Open your Gen AI Agent dashboard and go to the **Agents** tab as shown below:

   ![Gen AI Agent Dashboard](path/to/image1.png)

2. Click on the Agent created and select the **Endpoints** tab on the left-hand side of the screen as shown below:

   ![Select Endpoints Tab](path/to/image2.png)

3. On selecting the **Endpoints** tab, you will be able to see the endpoints as shown below:

   ![View Endpoints](path/to/image3.png)

4. Click on the endpoint and open it.
5. The OCID value shown here will be your `agentEndpointId` which we will be using going forward.

## Configuring a Digital Assistant

1. Open Oracle Digital Assistant instance.
2. Click the hamburger menu on the left-hand corner and go to **Settings > API Services**:

   ![Settings API Services](path/to/image4.png)

3. Press **Add Services** button to add the REST service to connect to Gen AI Agent from ODA.

   NOTE: Remember we need two APIs:
   - **Create a Session API** (which should be called once to get the session ID)
   - **Execute API** (to get the answer from Gen AI agents using session ID and agent ID)

4. Let's create the **Create Session API** first. Fill in the details as below and press **Create** button:
   - **Name**: genAiAgentCreateSession
   - **Endpoint**: `https://agent-runtime.generativeai.us-chicago-1.oci.oraclecloud.com/20240531/agentEndpoints/{agentEndpointId}/sessions`
   - **Method**: POST

   ![Create Session API](path/to/image5.png)

5. Once the API is created, go inside and select **Authentication Type** to `OCI Resource Principal` as shown below:

   ![Select Authentication Type](path/to/image6.png)

   In the body section add the below:
   ```json
   {
       "idleTimeoutInSeconds": 3600
   }
