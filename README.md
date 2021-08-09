# Detection-wafer-sensor-ML-Project

Due to file size constrains I have uploaded the Files on the Google Drive.

Google Drive Link:- https://drive.google.com/drive/u/0/folders/1p8s7vY7hnejoqDndcO5O_5MYYMs0AEsS

Due To Free Tier limitations, i have currently terminated the app, but if you want to check it,try to leave an message to my email:-tejame050@gmail.com

problem statement:-

To build a classification methodology to predict the quality of wafer sensors based on the given training data. 
The Instrumented Wafer (Thermocouples, Bonded Wafer or RTDs) finds application in semiconductor processing equipment where knowing and controlling the temperature at the surface of a wafer is critical. Inside the wafers they are multiple sensor which might be around 500-600 sensors.
If there is an issue or crash with the sensor or wafer.
It is such that we cannot take chance even if an single wafer fails to response and sensor are installed might be around to 10,000 – 1,00,000 approximately on device. Such that our model will try to know the error or crash about the sensor or wafer to get an particular report based on it.

Aim:-
To determine which wafer is an default one and to take an action if anything is default/error in wafer. Once it predict the output depending on it further action can be taken.

DATA SHARING AGREEMENT:-

Before starting any project there will be an data sharing agreement between both the parties such that it need to include all the details and it carry according in that specific manner it follows:-

Name validation:- try to validate the name in particular file name if that criteria does not satisfy, we will try to drop that file.

Number of columns:- As per DSA we will try to check whether we are getting same set of columns even if the client try to send the new dataset.

Name of column: it should contain the same name as per the schema file.

Null values in columns:-  if it contains null values in particular it need to be mentioned in that DSA itself, otherwise we will notify the client and dump that file as it not mentioned in DSA.

Pipeline:-

Try to build an system from one end it is going to inject an data on the first layer it will try to check the file name is good or not. It is just rough pipeline to understand it we have drawn it into our convince.
Suppose while building the model we will try to send the data to respective cluster or model. maybe perform clustering or grouping operation over there.
Similar for the test data we need to perform the same pipeline.
this pipeline need to perform on single click with an everything need to be generated (not looking for manual intervention just looking for automation..

Data description:-

Client try to send the datasets in the multiply set of files in batches .it will contain wafer names and 590 columns of different sensors values for each wafer, last column will have good or bad wafer .
Good/bad column will have unique values +1 and -1.
Apart from training files, we also require a "schema" file from the client, which contains all the relevant information about the training files such as: 
       Name of the files, Length of Date value in Filename, Length of Time value in Filename, Number of  Columns, Name of the Columns, and their datatype.

Data insertion into database:-

1) Database Creation and connection - Create a database with the given name passed. If the database is already created, open the connection to the database. 

2) Table creation in the database - Table with name - "Good_Data", is created in the database for inserting the files in the "Good_Data_Folder" based on given column names and datatype in the schema file. If the table is already present, then the new table is not created and new files are inserted in the already present table as we want training to be done on new as well as old training files.     

3) Insertion of files in the table - All the files in the "Good_Data_Folder" are inserted in the above-created table. If any file has invalid data type in any of the columns, the file is not loaded in the table and is moved to "Bad_Data_Folder".

Model training:-

1) We will  try to pull all the data from database where it will insert all the good data folder and the bad data folder it will automatically pull out.

2) Null values in the columns:- try to call different imputation as we are using Knn imputer. This imputation helps us to find the null values.

3) Between the model training we perform different transformation 

Data pre-processing:      

1) Check if any column has zero standard deviation such that it does not give any relationship in dataset . As it contain zero standard deviation.

2) After train and test we will try to divide the data into 3 sets(suppose), on basis of clustering algorithm.

3) Clustering:- here k-means is selected to build an k-mean we need to find out the k, it can be done using an elbow plot . But here system will automatically select the k-value. Here using knee locator, further the k-mean model is trained and used for pre-processed data and model is saved for prediction.

4) Model selection;- auto evaluation technique is used such it will evaluate each and every technique, since if we have three dataset each dataset might have decision tree, random forest or xg boost such that it will select the model which is best among the cluster, such that it will have custom ML technique.

Prediction:-

1) it will go through the entire pipeline such that Name of the files, Length of Date value in Filename, Length of Time value in Filename, Number of Columns, Name of the Columns and their datatype.

2) we also require a "schema" file from client which contains all the relevant information about the training files.

3) Based on the cluster number, the respective model is loaded and is used to predict the data for that cluster.

4) Once the prediction is made for all the clusters, the predictions along with the Wafer names are saved in a CSV file at a given location and the location is returned    to the client.

Deployment:-

We will be deploying the model to the Pivotal Cloud Foundry platform. 




