# A very simple Sentiment Analysis application

### This is one kind of a general framework for you to follow in order to deploy your machine learning model into production either using AWS, GCP, Azure or any other cloud tech of your choice. The process would remain similar

# This repo uses Docker, Flask and AWS to deploy the application.

## Steps:

1. Write your core source code that has all the computations, machine learning models and data preprocessing steps
2. Train and save your Machine Learning Model. I used ````pickle```` to save it but you may use other formats as well
3. Once you saved your models it is time to choose your backend web framework. I have chosen Flask for this application
4. You can use the same structure for your code as well and replace my code with yours. Just keep the overall template(function definitions and other imports) as it is.
5. Basically you would need write```@app.route("/")``` and add all your code inside functions under these decorators
6. For this applicaion, since it uses Docker we will be creating a Docker file
7. Each line of the Docker file is same as executing a line on your command prompt/terminal. Comments have been provided inside the Docker file explaining each line.
8. To run the Flask app type ```python app.py``` and then you should get a link http://0.0.0.0:8080/ that you can open in your browser.
9. To run the ML model and obtain the predictions navigate to http://0.0.0.0:8080/train_predict and hit refresh to see a new result each time 
10. Execute the following lines to build the docker image and run it locally. Skip this step if you do not want to test it on your local machine
    ```
    docker build -t "your_image_name_here" .
    docker run -d -p host_port:container_port "name_of_your_running_container"
    ```
11. Deploying using AWS Elastic Beanstalk
    - Create an AWS account for yourself, it is free. You will be charged once you deploy your app and cross the free tier limit for you account.
    - Follow this tutorial here https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install.html to install the ````eb cli```` client 
    - Once the ````eb cli```` is installed run the following commands as shown below.
    - I have selected all the default options, feel free to choose your own.

12. It will take a couple of minutes and then you should see a URL link to your app that is deployed on AWS


```
$ eb init

Select a default region
1) us-east-1 : US East (N. Virginia)
2) us-west-1 : US West (N. California)
3) us-west-2 : US West (Oregon)
4) eu-west-1 : EU (Ireland)
5) eu-central-1 : EU (Frankfurt)
6) ap-south-1 : Asia Pacific (Mumbai)
7) ap-southeast-1 : Asia Pacific (Singapore)
8) ap-southeast-2 : Asia Pacific (Sydney)
9) ap-northeast-1 : Asia Pacific (Tokyo)
10) ap-northeast-2 : Asia Pacific (Seoul)
11) sa-east-1 : South America (Sao Paulo)
12) cn-north-1 : China (Beijing)
13) us-east-2 : US East (Ohio)
14) ca-central-1 : Canada (Central)
15) eu-west-2 : EU (London)
(default is 3): 3

Select an application to use
1) [ Create new Application ]
(default is 1): 1

Enter Application Name
(default is "Elastic-Beanstalk-Docker-Flask"): your_app_name_here
Application your_app_name_here has been created.

It appears you are using Docker. Is this correct?
(Y/n): Y

Select a platform version.
1) Docker 17.06.2-ce
2) Docker 17.03.2-ce
3) Docker 1.12.6
4) Docker 1.11.2
5) Docker 1.9.1
6) Docker 1.7.1
7) Docker 1.6.2
8) Docker 1.5.0
(default is 1): 1
Note: Elastic Beanstalk now supports AWS CodeCommit; a fully-managed source control service. To learn more, see Docs: https://aws.amazon.com/codecommit/
Do you wish to continue with CodeCommit? (y/N) (default is n): n
Do you want to set up SSH for your instances?
(Y/n): Y

Select a keypair.
1) [ Create new KeyPair ]
(default is 1): 1

$ eb create name_you_environment_here

```

# Congrats you have deployed your very own Sentiment Analysis App!

#### Regarding the ****ml_model**** folder, I have trained a simple Machine Learning Model to classify the Sentiment of IMDb reviews downloaded from the Kaggle website and saved the vectorizer and also the model as pickle files to be used for prediction



