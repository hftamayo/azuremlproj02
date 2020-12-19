# Configuring and implementing a cloud based Machine Learning Production Model
## Machine Learning Engineer with Microsoft Azure Program
### Scholarship recipient: Herbert Fernández Tamayo

## Overview of the project
The project has two components, the first one is the automation of a Machine Learning Model and its implementation on the cloud using Azure Containers, the model is available via API functions and it has a dashboard avaiable using Application Insights Options. The model was tested using Apache Benchmark.

The second component is the implementation of a pipeline, the source code is available using a jupyter notebook file, it includes the provision of an Infrastructure as a service, configure an AutoML workspace, a model training stage and access to the expected results.

Both components use the same dataset.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:


# Project 1: Implement a cloud based Machine Learning Model

## Project's main goal:
To implement an automated ML model in production which is accesible via HTTP and its capable of establish interaction using API methods

## Part 1: Authentication
*Main goal*: Enable authentication in Azure ML workspace in order to execute a group of special operations. 

*Disclaimer*: you will need to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, you will create a Service Principal account and associate it with your specific workspace. 

Whether you are using an Azure ML studio account with no rights of deploy a Service Principal you may skip this step.

## Part 2: Automation of the Machine Learning Experiment
*Main goal*: to implement a model that will be cloud based deploy and consume as an endpoint. 

*A. Checkpoints to be considered*: 

    1. Create a new Automated Machine Learning run
    2. Select (in case it is available) or upload the bankmarketing dataset (https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv)
    3. Create a new Machine Learning experiment
    4. Configure a new compute cluster, it is suggested to choose the “Standard DS12 V2” type
    5. Adjust these specific parameters of the computer cluster:
        - Number of minimun nodes: 1
        - Run experiment as: Classification
        - Check “explain best model”
        - Exit criterion to 1
        - Concurrency to 5

*B. Screenshots of the execution of some stages*:

    1. Available datasets:
![step02_ss01.png](./img/s02/step02_ss01.png?raw=true "Available Datasets")

    2. Experiment completed:
![step02_ss02.png](./img/s02/step02_ss02.png?raw=true "Experiment completed")    
    
    3. Best model identified once the experiment is completed:
![step02_ss03.png](./img/s02/step02_ss03.png?raw=true "Best Model")    
    
        
## Part 3: Deploy the best model
*Main goal*: to publish via HTTP the best model identified and chose after the AutoML experiment is completed. 

*A. Checkpoints to be considered*: 

    1. Select the best model and click on “deploy”
    2. Enable authentication
    3. Deploy the model using Azure Container Instance (ACI)
    4. Whether the process is successful you may check in the “endpoints” option the recently deployment
    5. Click on it and you should get details about the REST Endpoint as well as its authentication keys.

*B. Screenshots of the execution of some stages*:

    1. Selection of the best model and click on Deploy:
![step03_ss01.png](./img/s03/step03_ss01.png?raw=true "Best Model and click on deploy")    

    2. Deploy on Azure Container Instance and enable authentication:
![step03_ss02.png](./img/s03/step03_ss02.png?raw=true "Deploy on Azure Container Instance")    

    3. Confirmation of “success” of the process of deploy:
![step03_ss03.png](./img/s03/step03_ss03.png?raw=true "Deploy process finised")    

    4. Checking the “Endpoint” option on ML Studio (by default the application insights are disabled):
![step03_ss04.png](./img/s03/step03_ss04.png?raw=true "Endpoin details")    

    5. Details how to “consume” the Endpoint:
![step03_ss05.png](./img/s03/step03_ss05.png?raw=true "How to consume and endpoint")    

![step03_ss06.png](./img/s03/step03_ss06.png?raw=true "How to consume and endpoint")    

        
## Part 4: Enable application insights
*Main goal*: Enable application insights and logging via source code (Although this process may be accomplished using the GUI).

*A. Checkpoints to be considered*: 

    1. It is important to check if az, Python SDK are enabled
    2. Download from Azure ML Studio the JSON file that contains the information of the subscription
    3. Write code that enables the application insights(see logs.py)
    4. In order to execute logs.py you need to confirm your user’s credentials
    5. Run logs.py and whether it successfully run check if the Application insights are enabled
    6. Click on the URL of the Application insights to see the results

*B. Screenshots of the execution of some stages*:

    1. Downloading config.json
![step04_ss01.png](./img/s04/step04_ss01.png?raw=true "Downloading config.json")    

    2. Execution of logs.py (2 y 3)
![step04_ss02.png](./img/s04/step04_ss02.png?raw=true "Executing logs.py")    

![step04_ss03.png](./img/s04/step04_ss03.png?raw=true "Executing logs.py")    

    3. Check the application insights URL enabled 
![step04_ss04.png](./img/s04/step04_ss04.png?raw=true "App insights enabled")    

    4. App insights results (5 y 6)
![step04_ss05.png](./img/s04/step04_ss05.png?raw=true "App insights results")    

![step04_ss06.png](./img/s04/step04_ss06.png?raw=true "App insights results")    

    
## Part 5: Swagger documentation
*Main goal*: To test the recently deployed model using Swagger.

*A. Checkpoints to be considered*: 

    1. Download the swagger.json file from the recently deployed model
    2. Copy swagger.json file in the same folder of swagger.sh and serve.py
    3. Run swagger.sh and serve.py
    4. Interact with the swagger instance based in the documentation obtained from the model.
    5. Display the content of the API model

*B. Screenshots of the execution of some stages*:

    1. Running swagger.sh
![step05_ss01.png](./img/s05/step05_ss01.png?raw=true "Running swagger.sh")    

    2. Accesing to swagger through localhost:9000
![step05_ss02.png](./img/s05/step05_ss02.png?raw=true "Accesing swagger")    

    3. Running serve.py
![step05_ss03.png](./img/s05/step05_ss03.png?raw=true "Running server.py")    

    4. Interacting with the swagger instance through the deployed model
![step05_ss04.png](./img/s05/step05_ss04.png?raw=true "Intaracting with swagger")    

    5. Available API methods 
![step05_ss05.png](./img/s05/step05_ss05.png?raw=true "Available API methods")    


![step05_ss06.png](./img/s05/step05_ss06.png?raw=true "Available API methods")    

## Part 6: Consume model endpoints
*Main goal*: To interact with the deployed model using a source code specifically designed for the purpose.

*A. Checkpoints to be considered*: 

    1. In the endpoint.py file update the values of scoring_uri and key obtained from the consume tab of the deployed model
    2. Execute the endpoint.py file
    3. A file called data.json should be created as a result of the interaction
    4. To test the performance of the endpoint run benchmark.sh file, do not forget to update the values of scoring_uri and key as well.

*B. Screenshots of the execution of some stages*:

    1. Scoring_uri and key values obtained from the consume tab of the deployed model
![step06_ss01.png](./img/s06/step06_ss01.png?raw=true "Scoring URI and key values")    

    2. Updating endpoint.py
![step06_ss02.png](./img/s06/step06_ss02.png?raw=true "Updating endpoint.py")    

    3. Running endpoint.py
![step06_ss03.png](./img/s06/step06_ss03.png?raw=true "Running endpoint.py")    

    4. Content of data.json file
![step06_ss04.png](./img/s06/step06_ss04.png?raw=true "Content of data.json")    

    5. Running benchmark.sh
![step06_ss05.png](./img/s06/step06_ss05.png?raw=true "Running benchmark.sh")    
        
        
# Project 2: Create, publish and consume a pipeline

## Project's main goal:
To execute the different stages from a jupyter notebook file to implement a pipeline.

*A. Checkpoints to be considered*: 

    1. Use the previous created experiment
    2. Upload the jupyter notebook file
    3. Downgrade from SDK ver 1.19 to 1.18
        - pip list | grep 1.19.0 | xargs pip uninstall -y
        - pip install azureml-sdk[automl,contrib,widgets]==1.18.0
        - pip install azureml-widgets==1.18.0
    4. Make sure config.json file is still in the same working directory
    5. Exexute each cell of the juputer notebook
    6. Verify the pipeline has been created
    7. Verify the pipeline is running

## Standout Suggestions
1. Implement the automation model using Kubernetes.
2. Develop different source code examples to interact in detail with the model using an Frontend framework such as React.js 
