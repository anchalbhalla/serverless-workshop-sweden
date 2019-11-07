# mustache-filter 

Create a mustache filter similar to a Snapchat filter by following these steps and visit the IBM developer code pattern for detailed steps (https://developer.ibm.com/tutorials/learn-serverless-computing-app-filter-mustache/): 


## Pre requisites 

* Install python version 3.x  
https://www.python.org/downloads/

* Intall opencv  
```
pip install opencv-python
```
* Install numpy 
```
python3 -m pip install numpy
```

* An IBM Cloud Account (https://cloud.ibm.com/) 

* Run Install Certificates.command in Applications / Python3.7


## Steps 

1. Create an IBM Cloud account 

2. Create a Functions service from the catalog
* ![alt text](https://github.com/anchalbhalla/mustache-filter/blob/master/images/function.png)
 
    * Go to Actions and create a namespace if you haven't already created one. Select location as either Dallas or Germany: 
    ![alt text](https://github.com/anchalbhalla/serverless-workshop-sweden/blob/master/namespace-create.png)  
    
    * Once that's done, Create an Action by clicking create: 
     ![alt text](https://github.com/anchalbhalla/serverless-workshop-sweden/blob/master/action-create.png) 
     
     * Give a name to the action and select the runtime as python 3: 
     ![alt text](https://github.com/anchalbhalla/serverless-workshop-sweden/blob/master/action-create-1.png)
    

3. Copy paste this python code to the Code section of the service:  
``` 

#
#
# main() will be run when you invoke this action
#
# @param Cloud Functions actions accept a single parameter, which must be a JSON object.
#
# @return The output of this action, which must be a JSON object.
#
#
import sys 
import random

def main(dict):
    mus_urls = ['https://sublimerobots.com/wp-content/uploads/2014/12/mustache.png', 'https://i.pinimg.com/originals/67/2e/0f/672e0f6f71ebe08a5029a89e85df1e18.png', 'https://images.vexels.com/media/users/3/130978/isolated/lists/f932a333154f1d6bff554c1010466f00-hipster-mustache-5.png', 'https://www.papilbo.com/2743-large_default/basic-classi-con-fiocco-blu.jpg', 'https://www.660citynews.com/wp-content/blogs.dir/sites/8/2016/11/01/moustache.png' ]

    index = random.randint(0, len(mus_urls)-1)
    print(mus_urls[index])  
 
    return {'url':mus_urls[index]}
  
```
   
   * Save the code 
   
   * Enable Web Action under Endpoints and copy the HTTPS URL that is the first URL - this URL will be used in the python application to do get the different filters for the application
   ![alt text](https://github.com/anchalbhalla/serverless-workshop-sweden/blob/master/web_action.png) 
   
   

   
4. Download the serverless-detection.py and the haar cascade files. Click on the green colour 'clone or download' button on the top right to download all the files in a zip folder. Extract the folder to retrieve the files 


5. Edit the serverless-detection.py file: 
   
   * Change your API location accordingly, if your namespace is in eu.de (Germany) use "eu-de.functions.cloud.ibm.com"  otherwise use "eu-gb.functions.cloud.ibm.com" if it is in Great Britain (this is set as default in the file).
   * Add your HTTPS URL (not the REST API link) from the Cloud Functions service on the 18th line of the code
   * Add .json at the end of the URL

6. Run the following command on the terminal to execute the application: 

``` 
python3 serverless-detection.py 
``` 



## The Architecture 
![alt text](https://github.com/anchalbhalla/mustache-filter/blob/master/images/Picture1.png)


## The Process 
![alt text](https://github.com/anchalbhalla/mustache-filter/blob/master/images/process-Diagram.png)
