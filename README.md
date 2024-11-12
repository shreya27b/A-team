# AI-Powered Real-Time Maintenance
Fabric-based real-time analytics solution streaming CNC machine data, applying AI for predictive maintenance, and triggering alerts to prevent failures, optimizing efficiency and reducing downtime.

Imagine a bustling factory floor, where precision and efficiency are critical to keeping the operation running smoothly. In such an environment, CNC machines are the heart of production, tirelessly performing complex manufacturing tasks. However, unexpected failures can lead to costly downtime and reduced productivity. This is where our AI-driven predictive maintenance solution steps in—designed to prevent disruptions by constantly monitoring machine health and predicting potential issues before they occur.

# Architecture
![image](https://github.com/user-attachments/assets/1a8f7216-52ec-4903-aeca-df3f817cd9a7)


# Real-Time Intelligence
We have leveraged real-time intelligence to stream the CNC machines’ data from a custom endpoint as the source, simulate the CNC data, and push it to the KQL DB staging table.
To simulate the data and send it to the custom endpoint, we have leveraged a notebook named ‘SimulateCNCData’.

# Data Science
Once we have the data in the staging table, we apply our AutoML model to predict the probability of various types of failures, such as heat dissipation failure, power failure, temperature failure, etc.
The predicted data will be pushed to the final fact table. This operation will be performed by calling the notebook ‘CallMLModel’.

# Real-time Dashboard
Once we have the data in the final table, we will build a dashboard. On our dashboard, you can see crucial metrics at a glance: the total number of active machines, those currently under maintenance, and a detailed view of machines running in various regions. We can even drill down into specific health parameters for each machine, identifying potential issues such as overheating or excessive strain.
 ![image](https://github.com/user-attachments/assets/b2dd2029-1c29-47aa-b15a-71931826432d)
![image](https://github.com/user-attachments/assets/f2e15a50-71bb-4482-ba99-40ca29c53563)


# Data Activator
If the AutoML model detects anomalies or a high risk of failure, the system immediately sends alerts through the Data Activator. Users are notified about the nature of the issue and advised on the necessary precautions to prevent breakdowns. For example, if the model predicts a heat dissipation failure, the operator will receive a warning along with recommendations for mitigating the risk.
