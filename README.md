# Configuring and implementing a cloud based Machine Learning Production Model
## Machine Learning Engineer with Microsoft Azure Program
### Scholarship recipient: Herbert Fernández Tamayo

*TODO:* Write an overview to your project.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step. An architectural diagram is an image that helps visualize the flow of operations from start to finish. In this case, it has to be related to the completed project, with its various stages that are critical to the overall flow. For example, one stage for managing models could be "using Automated ML to determine the best model". 

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
        

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
