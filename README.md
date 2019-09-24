# WORK IN PROGRESS
# Monitor your ML Models using Watson OpenScale

Businesses today are increasingly certain that AI will be a driving force in the evolution of their industries over the next few years. To successful infuse AI into your product or solution, there are many that factors that challenges its widespread adoption in the business and achieve their expected outcomes. A few listed below-

  1. Building Trust- Organisations and businesses tend to be skeptical about AI because of its "black box" nature. Because of this many promising models don't go into production.
  2. Algorithm bias- Another inherent problem with AI systems is that they are only as good – or as bad – as the data they are trained on. If the input data is filled with racial, gender, communal or ethnic biases your model's accuracy is going to eventually drift away.
  3. Making Decisions Explainable- How can the model prove the reasoning behind the it's decision-making? It is critical that AI outcomes are fully explainable by keeping a complete track of inputs and outputs of any AI-powered application.  

What if there is one console that makes it easier for business users to track and measure AI outcomes? 

In this Code Pattern we demonstrate a way to Monitor your AI models in an application using Watson OpenScale. This will be demonstrated with an example of a Telecomm Call Drop Prediction Model. After the user has completed the code pattern, they will learn-

  * How to store custom models using open source technology on Watson Machine Learning.
  * How to deploy a model and connect the model deployment to Watson OpenScale on Cloud Pak for Data and on IBM Cloud.
  * How to setup Model Fairness and Model Quality montiors and Watson OpenScale on Cloud Pak for Data and on IBM Cloud, using   python notebook.
  * How to create a project and setup a python notebook on Cloud Pak for Data.
  
## Pre-requisites
* [IBM Cloud Pak for Data](https://www.ibm.com/in-en/products/cloud-pak-for-data) 
* [OpenScale add-on for Cloud Pak for Data](https://cloud.ibm.com/docs/services/ai-openscale-icp?topic=ai-openscale-icp-inst-install-icp )

## Architecture Diagram
  
![](doc/src/images/Architecture_Diagram.png)

1. Data stored into Cloud Pak for Data internal Db.
2. The joined data is stored back to the Internal Db of Cloud Pak for Data and Assigned to the current working project.
3. Create ML Models using Jupyter Python Notebooks to predict Call Drop, for one cell tower at a time.
4. Model trained and/or stored in Watson Machine Learning, which is also connected to the AI OpenScale.
5. Configure Fairness, Quality and Explainability Montiors for each Tower's model, present within Cloud Pak for Data or on other external Clouds (Multi-Cloud Architecture).


## Steps
1. [Create a new Project on your Cloud Pak for Data instance](1-create-a-new-project-on-your-cloud-pak-for-data-instance)
2. [Add a new Watson Machine Learning Model]()
3. [Create a new Python Notebook on your Cloud Pak for Data Project]()
4. [Configure Watson OpenScale on Cloud Pak for Data]()
7. [Create a new Project in your IBM Cloud Pak for Data instance]()
8. [Run the Inital Scoring and Payload Logging]()
9. [Configure the Quality and Fairness Monitors on Watson OpenScale]()
10. [Add Feedback Data to setup your dashboard on Watson OpenScale]()


### 1. Create a new Project on your Cloud Pak for Data instance

* Once you login to your Cloud Pak for Data instance. Click on the `menu` icon in the top left corner of your screen and then click on `Projects`.
   ![](doc/src/gif/gotoproject.gif)
   
* When you reach the Project list, click on `New Project`. You will get a pop-up, make sure to have the `Analytics Project` option and enter the desired name. Once you click on `Ok` you will go to a new screen. Click on `Create` to complete your project creation.

### 2. Add a new Watson Machine Learning Model

* Create a new [Watson Machine Learning](https://cloud.ibm.com/catalog/services/machine-learning) instance on IBM Cloud. Log in to IBM Cloud or sign up for IBM Cloud if you don't have an account by following the on-screen instructions.

* Select the location to `Dallas` region and hit create.
  ![](doc/src/gif/createwml.gif)
* Once the instance is created. Click on `Service Credentials`. Click on `New Credentials` and then click on `View Credentials`. Copy using the icon. 
  ![](doc/src/gif/copycred.gif)

```
NOTE: Save the credentials. It will be required during the later stages.
```

### 3. Create a new Python Notebook on your Cloud Pak for Data Project

 * Go back to your Cloud Pak for Data Project Landing Page.
 * Click on `Notebook>Add Notebook`.
  ![](doc/src/gif/createnotebook.gif)
 * Go to the `From URL` tab and enter the notebook URL- https://github.com/IBM/icp4d-telco-monitor-models-with-wml-openscale/blob/master/notebook/Setup_your_AIOS_Dashboard.ipynb
 
  ![](doc/src/images/url_notebook.png)
  

### 4. Configure your Python Notebook

 ```
 Note: The following steps are very important. Be sure to not miss any of them. Also, it is recommended that you run each cell one by one in the notebook.
 ```
 
 1. [Install the Necessary Packages](#4.1-install-the-necessary-packages)
 2. [Configure the Necessary Details](#4.2-configure-the-necessary-details)
 3. [Add the dataset](#4.3-add-the-dataset)
 4. [Add the subscription id](#4.4-add-the-subscription-id)
 #### 4.1 Install the Necessary Packages
 
 * Click on the `Run` icon and install the necessary packages given in each cell.
 * Next, restart your kernel by either clicking the restart icon or `Kernel>Restart`.
 
 #### 4.2 Configure the Necessary Details
 
 * Under `Section 2.1 Global Variables` enter the following-
    a) Your desired Model Name
    b) Your desired Model Deployment Name
    c) The name of an `empty` schema in your database
    ```
    Note: Pls make sure you have an empty schema, ie has no content at all in it. 
    ```
 * Under `Section 2.3 Add your WML Credentials`. Add the credentials you had copied earlier in a previous step, while creating the instance.
 * Under `Section 2.4 Update your AIOS Credentials`. Add the necessary instance details as instructed in the cell.
    a) Replace the <> with the information within the brackets.
 * Under `Section 2.5 Add your Db Credentials`. Add your db credentials and make sure the keys given in the template have     values filled in. (ie, hostname, username, db, port, etc.)
 
 #### 4.3 Add the Dataset
 
 * Go back to your Project Landing Page. 
 * Clone this repo, by clicking on `Clone or Download`, unzip it and navigate to the `datasets` folder.
 * In your Project Page. Click on `Dataset>Add new Dataset> Browse`. Select the dataset downloaded.
   ![](doc/src/gif/adddataset.gif)
    
 * Now, open your notebook again and click on the cell under `Section 2.2 Add Dataset`.
 * Click on the `10/01` icon and select the `Insert to code` option. Under that select `Insert Pandas Dataframe` option.
    ![](doc/src/image/add_dataset.png)
    
  #### 4.4 Add the Subscription Id

  * Now Start Running the notebook from `Section 1.2 till the end of Section 4.5`
  * Before runnning the remaining (again, pls keep in mind it is better run cell by cell), update the variable `subscription_id` under `Section 2.6`, with id you have just created.
  * You will find this id in the table above, as instructed in the notebook.
  * Now, run the rest of the notebook till the end.
    
 

## Sample Output


