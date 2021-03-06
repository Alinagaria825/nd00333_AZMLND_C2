# Operationalizing Machine Learning

## Project Overview
In this project, we demonstrate how to Operationalize Machine Learning in Azure ML Studio. Here I used the [Bank Marketing dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv) to create an Automate ML run experiment, then deployed the best model generated from the run. I obtained the REST endpoint for the best model and the Swagger documentation for the model and then I was able to consume the model endpoint. Finally, I created, deployed, and publish a pipeline with the help of the Python SDK.

## Architectural Diagram
![azureml](screenshots/azureml_architecture.png)

## Key Steps

1. Authentication: I used the lab provided by udacity to complete this section, thus no screenshots are provided here for authentication as it is already implemented in the virtual lab.

2. Automated ML Experiment: Here I used the [Bank-Markerting dataset](https://automlsamplenotebookdata.blob.core.windows.net/automl-sample-notebook-data/bankmarketing_train.csv).

    - I uploaded the dataset and registered it in Azure ML Studio and I used column "y" as the target column.
    - Here is an image fo the Registred Dataset in Azure ML Studio. ![dataset](screenshots/dataset.JPG)
    - Created a new experiment with name *bank-marketing-exprt* ![model](screenshots/complete_run.JPG)
    - Created new cluster *auto-ml* with Standard_DS12_v2 for the Virtual Machine Size and selected 1 as the number of minimum nodes.
    - Run the experiment using *Classification*, set *Exit criterion* to 1 hour and reduced *Concurrency* to 1.

3. Deploy the best model: After a successfull run of the bank-marketing-exprt, we obtained the bet model algorithm *VotingEnsemble* ![deploy](screenshots/deployment.JPG)
    - We then deploy the model in an Azure Container Instance.
    - I named the deployment *bank-model-deploy* and enable authentication to securely deploy the model.
4. Enable logging: The model was sucessfully deployed and then I ran the *logs.py*
    - I also enabled Application Insights in this file with the code `service.update(enable_app_insights=True)`. ![insights](screenshots/AppInsights.JPG)
    - The `logs.py` file ran correctly producing logs as in the screenshot.
    ![log1](screenshots/logs.JPG) ![log2](screenshots/logs2.JPG) ![log3](screenshots/logs3.JPG)
 
5. Swagger Documentation: After a successful model deployment I could obtan the endpoint rest API including the *swagger.json* file generated.
    - I downloaded the `swagger.json` file into the swagger directory.
    - Then from the Git Bash terminal I ran the cmmand `bash swagger.sh` from the swagger directory to start the wagger documnetation API service.
    - I then ran the `serve.py` file to serve the swagger.json file holdint the HTTP API methods and response for the model.
    - Once the server is running I open he browser and run `http://localhost:9000`, then in the Swagger instance running, I explore our *swagger.json* file at, `http://localhost:8001/swagger.json`
    ![swagger](screenshots/swagger1.JPG)
    ![swagger2](screenshots/swagger2.JPG)

    - The model payload response is as below
    ![model_payload](screenshots/model_payload.JPG)
    ![model_payload1](screenshots/model_payload1.JPG)
    ![model_payload2](screenshots/model_payload2.JPG)


6. Consume model endpoints; With the swagger instance running correclty, we can now conum the endpoint
    - I obtaned the scoring URI and key generated after the deplyment and updated the `endpoint.py` file.
    - From new a powershell terminal, I navigated to the project files and ran the `python endpoint.py`  and got the results in the screenshot below. 
    ![endpoint](screenshots/endpoint.JPG)
    - After running the endoint.py file, I obtained a json paylod in the file `data.json`
    - I updated the `benchmark.sh` with the generated scoring URI and key.
    - Next I also ran the *banchmark.sh* file from a new Git bash terminal with the command `bash benchmark.sh`, and got the following.
    ![benchmark](screenshots/benchmark.jpg)

7. Create and publish a pipeline: I crted an published a pipline  runninng the notebook file provided in the project files.
    - First I uploaded the Jupyter notebook, `aml-pipelines-with-automated-machine-learning-step.ipynb`, to Azure ML Studio.
    - I created an expriment, *bank-marketing-exprt* and published pipline. ![pipeline](screenshots/pipeline_complete.JPG)
    - The Bank-Markting dataset and the AutoML module are highligted in the imaeg above. 
    - Here is n image for the *Published Pipeline overview* showing the REST endpoing and a status of ACTIVE. ![active](screenshots/pipeline_endpint.JPG)
    - The Jupyter Notebook includes the “Use RunDetails Widget”. ![rundetails](screenshots/run_details.JPG)
    - Pipeline published from the notebook. ![pipe](screenshots/pipe.JPG)

8. Documentation: This README.md document contains:
    - Project Overview
    - Architetural Diagram
    - Screenshots of project main steps with shorta descriptions
    - Suggettion for improvemnt
    - Link to screencast

## Screen Recording
I made a short screencast available in the link [here](https://youtu.be/UfYqLiJg8yc) showing the:
- Deployed Model
- Deployed Pipeline
- Automated ML Model
- API request to the endpoint with json payload.

## Standout Suggestions
To improve for future us, we can get more data sameple point for the dataset to enhance the model.
