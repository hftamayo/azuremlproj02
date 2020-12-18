# Configuring and implementing a cloud based Machine Learning Production Model
## Machine Learning Engineer with Microsoft Azure Program
### Scholarship recipient: Herbert Fernández Tamayo

*TODO:* Write an overview to your project.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Part 1: Authentication
*Main goal*: Enable authentication in Azure ML workspace in order to execute a group of special operations. 

*Disclaimer*: you will need to install the Azure Machine Learning Extension which allows you to interact with Azure Machine Learning Studio, part of the az command. After having the Azure machine Learning Extension, you will create a Service Principal account and associate it with your specific workspace. 

Whether you are using an Azure ML studio account with no rights of deploy a Service Principal you may skip this step.

## Part 2: Automation of the Machine Learning Experiment
*Main goal*: to implement a model that will be cloud based deploy and consume as an endpoint. 

*Checkpoints to be considered*: 

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

*Screenshots of the execution of some stages*:

    1. Available datasets:
    2. Experiment completed:
    3. Best model identified once the experiment is completed:
        
        
## Part 3: Deploy the best model
*Main goal*: to publish via HTTP the best model identified and chose after the AutoML experiment is completed. 

*Checkpoints to be considered*: 

    1. Select the best model and click on “deploy”
    2. Enable authentication
    3. Deploy the model using Azure Container Instance (ACI)
    4. Whether the process is successful you may check in the “endpoints” option the recently deployment
    5. Click on it and you should get details about the REST Endpoint as well as its authentication keys.

*Screenshots of the execution of some stages*:

    1. Selection of the best model and click on Deploy:
    2. Deploy on Azure Container Instance and enable authentication:
    3. Confirmation of “success” of the process of deploy:
    4. Checking the “Endpoint” option on ML Studio (by default the application insights are disabled):
    5. Details how to “consume” the Endpoint: (fotos 5 y 6)
        
## Part 4: Enable application insights
*Main goal*: Enable application insights and logging via source code (Although this process may be accomplished using the GUI).

*Checkpoints to be considered*: 

    1. It is important to check if az, Python SDK are enabled
    2. Download from Azure ML Studio the JSON file that contains the information of the subscription
    3. Write code that enables the application insights. See logs.py
    4. In order to execute logs.py you need to confirm your user’s credentials
    5. Run logs.py and whether it successfully run check if the Application insights are enabled
    6. Click on the URL of the Application insights to see the results

*Screenshots of the execution of some stages*:

    1. Download config.json
    2. Execution of logs.py (2 y 3)
    3. Check the application insights URL enabled 
    4. App insights results (5 y 6)

## Part 5: Swagger documentation
*Main goal*: To test the recently deployed model using Swagger.

*Checkpoints to be considered*: 

    1. Download the swagger.json file from the recently deployed model
    2. Copy swagger.json file in the same folder of swagger.sh and serve.py
    3. Run swagger.sh and serve.py
    4. Interact with the swagger instance based in the documentation obtained from the model.
    5. Display the content of the API model

*Screenshots of the execution of some stages*:

    1. Running swagger.sh
    2. Accesing to swagger through localhost:9000
    3. Running serve.py
    4. Interacting with the swagger instance through the deployed model
    5. Available API methods (5 y 6) 
        
## Part 6: Consume model endpoints
*Main goal*: To interact with the deployed model using a source code specifically designed for the purpose.

*Checkpoints to be considered*: 

    1. In the endpoint.py file update the values of scoring_uri and key obtained from the consume tab of the deployed model
    2. Execute the endpoint.py file
    3. A file called data.json should be created as a result of the interaction
    4. To test the performance of the endpoint run benchmark.sh file, do not forget to update the values of scoring_uri and key as well.

*Screenshots of the execution of some stages*:

    1. Scoring_uri and key values obtained from the consume tab of the deployed model
    2. Updating endpoint.py
    3. Running endpoint.py
    4. Content of data.json file
    5. Running benchmark.sh
        
## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
