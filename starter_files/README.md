*NOTE:* This file is a template that you can use to create the README for your project. The *TODO* comments below will highlight the information you should be sure to include.


# Operationalizing Machine Learning

In this project, you will continue to work with the Bank Marketing dataset. You will use Azure to configure a cloud-based machine learning production model, deploy it, and consume it. You will also create, publish, and consume a pipeline. In the end, you will demonstrate all of your work by creating a README file and a screencast video.

## Architectural Diagram
*TODO*: Provide an architectual diagram of the project and give an introduction of each step.

## Key Steps
*TODO*: Write a short discription of the key steps. Remember to include all the screenshots required to demonstrate key steps. 

1. Authentication: I used the lab provided by udacity to complete this section, thus no screenshots are provided here for authentication as it is already implemented in the virtual lab.

2. Automated ML Experiment: Here I used created a new Automated ML run, used the [Bank-Markerting dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv).

    - Created a new experiment with name *bank-marketing-exprt* ![]()
    - Created new cluster *auto-ml* with Standard_DS12_v2 for the Virtual Machine Size and selected 1 as the number of minimum nodes.
    - Run the experiment using *Classification*, set *Exit criterion* to 1 hour and reduced *Concurrency* to 1.

3. Deploy the best model
4. Enable logging
5. Swagger Documentation
6. Consume model endpoints
7. Create and publish a pipeline
8. Documentation

## Screen Recording
*TODO* Provide a link to a screen recording of the project in action. Remember that the screencast should demonstrate:

## Standout Suggestions
*TODO (Optional):* This is where you can provide information about any standout suggestions that you have attempted.
