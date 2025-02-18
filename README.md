# AI-900
Esse repositório diz respeito ao curso da DIO AI-900 sobre inteligência artificial e ML

As intruções seguidas foram as seguintes:

Sign into the Azure portal at https://portal.azure.com using your Microsoft credentials.

Select + Create a resource, search for Machine Learning, and create a new Azure Machine Learning resource with the following settings:
Subscription: Your Azure subscription.
Resource group: Create or select a resource group.
Name: Enter a unique name for your workspace.
Region: East US.
Storage account: Note the default new storage account that will be created for your workspace.
Key vault: Note the default new key vault that will be created for your workspace.
Application insights: Note the default new application insights resource that will be created for your workspace.
Container registry: None (one will be created automatically the first time you deploy a model to a container).
Select Review + create, then select Create. Wait for your workspace to be created (it can take a few minutes), and then go to the deployed resource.
Launch studio
In your Azure Machine Learning workspace resource, select Launch studio (or open a new browser tab and navigate to https://ml.azure.com, and sign into Azure Machine Learning studio using your Microsoft account). Close any messages that are displayed.

In Azure Machine Learning studio, you should see your newly created workspace. If not, select All workspaces in the left-hand menu and then select the workspace you just created.

Use automated machine learning to train a model
Automated machine learning enables you to try multiple algorithms and parameters to train multiple models, and identify the best one for your data. In this exercise, you’ll use a dataset of historical bicycle rental details to train a model that predicts the number of bicycle rentals that should be expected on a given day, based on seasonal and meteorological features.

Citation: The data used in this exercise is derived from Capital Bikeshare and is used in accordance with the published data license agreement.

In Azure Machine Learning studio, view the Automated ML page (under Authoring).

Create a new Automated ML job with the following settings, using Next as required to progress through the user interface:

Basic settings:

Job name: Job name field should already be prepopulated with a unique name. Keep it as is.
New experiment name: mslearn-bike-rental
Description: Automated machine learning for bike rental prediction
Tags: none
Task type & data:

Select task type: Regression
Select dataset: Create a new dataset with the following settings:
Data type:
Name: bike-rentals
Description: Historic bike rental data
Type: Table (mltable)
Data source:
Select From local files
Destination storage type:
Datastore type: Azure Blob Storage
Name: workspaceblobstore
MLtable selection:
Upload folder: Download and unzip the folder that contains the two files you need to upload https://aka.ms/bike-rentals
Select Create. After the dataset is created, select the bike-rentals dataset to continue to submit the Automated ML job.

Task settings:

Task type: Regression
Dataset: bike-rentals
Target column: rentals (integer)
Additional configuration settings:
Primary metric: NormalizedRootMeanSquaredError
Explain best model: Unselected
Enable ensemble stacking: Unselected
Use all supported models: Unselected. You’ll restrict the job to try only a few specific algorithms.
Allowed models: Select only RandomForest and LightGBM — normally you’d want to try as many as possible, but each model added increases the time it takes to run the job.
Limits: Expand this section
Max trials: 3
Max concurrent trials: 3
Max nodes: 3
Metric score threshold: 0.085 (so that if a model achieves a normalized root mean squared error metric score of 0.085 or less, the job ends.)
Experiment timeout: 15
Iteration timeout: 15
Enable early termination: Selected
Validation and test:
Validation type: Train-validation split
Percentage of validation data: 10
Test dataset: None
Compute:

Select compute type: Serverless
Virtual machine type: CPU
Virtual machine tier: Dedicated
Virtual machine size: Standard_DS3_V2*
Number of instances: 1
* If your subscription restricts the VM sizes available to you, choose any available size.

Submit the training job. It starts automatically.

Wait for the job to finish. It might take a while — now might be a good time for a coffee break!
