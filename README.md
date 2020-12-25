# Configuring and implementing a cloud based Machine Learning Production Model
### Machine Learning Engineer with Microsoft Azure Program
###### Scholarship recipient: Herbert Fernández Tamayo


### Table of Content
1. Project's overview
2. architectural Diagram
3. Screen Recording
4. Project 01: Implement a cloud based Machine Learning Model
4.1 Authentication
4.2 Automation of the Machine Learning Experiment
4.3 Deploy the best model
4.4 Enable application insights
4.5 Swagger documentation
4.6 Consume model endpoints
5. Project 02: Create, publish and consume a pipeline
5.1 Project's main goal:
6. Best practice: Cleaning the workspace
7. How to Improve the project in the future?

### 1. Project's overview
The project has two components, the first one is the automation of a Machine Learning Model and its implementation on the cloud using Azure Containers, the model is available via API functions and it has a dashboard avaiable using Application Insights Options. The model was tested using Apache Benchmark.

The second component is the implementation of a pipeline, the source code is available using a jupyter notebook file, it includes the provision of an Infrastructure as a service, configure an AutoML workspace, a model training stage and access to the expected results.

Both components use the same dataset.

### 2. Architectural Diagram
 The below diagram has been created using draw.io:
![project02_diagram.png](./project02_diagram.png?raw=true "Project diagram")

### 3. Screen Recording
In the next video the user may have access to the project's summary and the expected results. In the next sections, there are specific videos to help the user to understand specific tasks :

[Project's Summary](https://youtu.be/e9Z9gdNLemc)


### 4. Project 01: Implement a cloud based Machine Learning Model

*Project's main goal*:

To implement an automated ML model in production which is accesible via HTTP and its capable of establish interaction using API methods

### 4.1 Authentication
*Main goal*: 

Enable authentication in Azure ML workspace in order to execute a group of special operations. 

*Disclaimer*: 

You will need to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, you will create a Service Principal account and associate it with your specific workspace. 

Whether you are using an Azure ML studio account with no rights of deploy a Service Principal you may skip this step.

### 4.2 Automation of the Machine Learning Experiment
*Main goal*: 

To implement a model that will be cloud based deploy and consume as an endpoint. 

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
    
    
*C. Video tutorial*:

[Automation of the Machine Learning Experiment Part 1](https://youtu.be/izuIk1Qx7Ag)

[Automation of the Machine Learning Experiment Part 2](https://youtu.be/HP1focRImfY)


### 4.3 Deploy the best model
*Main goal*: 

To publish via HTTP the best model identified and chose after the AutoML experiment is completed. 

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

*C. Video tutorial*:

[Deploy the best model](https://youtu.be/veDdDgKgFf4)

      
### 4.4 Enable application insights
*Main goal*: 

Enable application insights and logging via source code (Although this process may be accomplished using the GUI).

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

*C. Video tutorial*:

[Enable application insights - Part 1](https://youtu.be/0SflRVTtTyw)

[Enable application insights - Part 2](https://youtu.be/69IZq83Pju0)

[Enable application insights - Part 3](https://youtu.be/6qiv6UYPdWc)


### 4.5 Swagger documentation
*Main goal*: 

To test the recently deployed model using Swagger.

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

*C. Video tutorial*:

[Swagger documentation - Part 1](https://youtu.be/yncXp4vOSrc)

[Swagger documentation - Part 2](https://youtu.be/WIUgUVIsVO0)

[Swagger documentation - Part 3](https://youtu.be/imS2sHPqyM8)


### 4.6 Consume model endpoints
*Main goal*: 

To interact with the deployed model using a source code specifically designed for the purpose.

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


*C. Video tutorial*:

[Consume model endpoints](https://youtu.be/bqObQt0onb4)

        
### 5. Project 02: Create, publish and consume a pipeline

### 5.1 Project's main goal:

To execute the different stages from a jupyter notebook file to implement a pipeline.

*A. Checkpoints to be considered*: 

    1. Use the previous created experiment
    2. Upload the jupyter notebook file
    3. Downgrade from SDK ver 1.19 to 1.18
        - pip list | grep 1.19.0 | xargs pip uninstall -y
        - pip install azureml-sdk[automl,contrib,widgets]==1.18.0
        - pip install azureml-widgets==1.18.0
    4. Make sure config.json file is still in the same working directory
    5. Execute each cell of the juputer notebook
    6. Verify the pipeline has been created
    7. Verify the pipeline is running


*B. Screenshots of the execution of some stages*:

    1. Error in the  execution of he jupyter notebook using SDK ver 1.19.0: output error
![errorjupyter.png](./img/s07/errorjupyter.png?raw=true "Error in the  execution of he jupyter notebook using SDK ver 1.19.0: output error")    

    2. Error in the  execution of he jupyter notebook using SDK ver 1.19.0: checking logs
![error experiment ml run.png](./img/s07/error experiment ml run.png?raw=true "Error in the  execution of he jupyter notebook using SDK ver 1.19.0: checking logs")    

    3. Downgrading from SDK ver 1.19 to 1.18
![step07_ss01.png](./img/s07/step07_ss01.png?raw=true "Downgrading from SDK ver 1.19 to 1.18")        
    
    4. After downgrade, the execution of the jupyter notebook was sucessful: pipelines completed
![step07_ss02.png](./img/s07/step07_ss02.png?raw=true "After downgrade, the execution of the jupyter notebook was sucessful: pipelines completed")        

    5. Pipeline deployed
![step07_ss03.png](./img/s07/step07_ss03.png?raw=true "Endpoint deployed")        
    
    6. Dataset avaiables in the ML studio's workspace
![step07_ss04.png](./img/s07/step07_ss04.png?raw=true "Dataset avaiables in the ML studio's workspace")        

    7. Training process completed
![step07_ss05.png](./img/s07/step07_ss05.png?raw=true "Training process completed")

    8. Automl model completed
![step07_ss06.png](./img/s07/step07_ss06.png?raw=true "Automl model completed")
    
    9. Automl model completed (view from the jupyter notebook)
![step07_ss07.png](./img/s07/step07_ss07.png?raw=true "Automl model completed_view from the jupyter notebook")

*C. Video tutorial*:

[Create, publish and consume a pipeline Part 1](https://youtu.be/WPAmaW4bsMg)

[Create, publish and consume a pipeline Part 2](https://youtu.be/IdzSo1Qx_Uk)

### 6. Best practice: Cleaning the workspace

    1. Deleting Computer Clusters instances
![cleaning01.png](./img/cleaning01.png?raw=true "Deleting computer clusters")        

    2. Deleting Computer instances
![cleaning02.png](./img/cleaning02.png?raw=true "Deleting computer instances")        

### 7. How to Improve the project in the future?
1. Deploy the best model calculated from the AutoML Experiment using Kubernetes instead ACI.
2. Update the notebook's sourcecode to be compatible with SDK 1.19.0.
3. Ppackage the registered Azure Machine Learning model with Docker
4. Add diferent datasets in endpoint.py to have more interaction with the deployed model .
