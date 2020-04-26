# Reddit flair detection

Hello, I am Himanshu Garg, a B. tech undergrad @ IIIT-D, majors in CSE.

Here, i am presenting a simple website which can take URL of any submission of Reddit/India and
suggest us the best suited Flair for the post using NLP. The website has been hosted on heroku for ease of use.

URL of the website - https://flairofreddit.herokuapp.com

# HOW to use ?

Website main page looks something like the below image.

<img width="1440" alt="home page of the website" src="https://user-images.githubusercontent.com/43913398/61592756-fc9c9180-abf4-11e9-8090-03d457c58d94.png">


1. In the URL box, Just enter the Submission URL, of which you want the most appropriate flair.
2. Tap on submit button.

<Strong> Voila!!! </Strong>  You will have the most appropriated FLAIR (tag) displayed in the Blue box.

<Strong> NOTE : </Strong> If it displays the message "check URL..." --> means the entered URL is <Strong> NOT </Strong> correct.


# Technology Stack ...

1. PYTHON is the man programming language that this web app is built on. All the NLP related word and backend of the website (FLASK) is based on python.

2. A little Cascading style sheets (CSS) and bootstrap has been used for the frontend.

# How to install it on your PC's

Just follow the below steps in order to run this web app offline on your computer.

1. Clone the repository on the system.
2. Open the terminal and go to the destination of the cloned file.
3. Type "cd website" in the terminal.
4. Enter "virtualenv venv"
5. Enter "source venv/bin/activate"
6. Enter "pip install -r requirements.txt"
7. Run "python app.py" from your terminal.

Here you go, the application is running on your terminal. <br>
Just open the displayed URL (on terminal) on your web browser.

# love BROWNIES !!!!
 I have also done some data analysis on reddit/India submissions posted from June 1st 2018 to October 1st 2018; which can be found at the above mentioned link - https://flairofreddit.herokuapp.com
 
 <img width="1440" alt="Screenshot 2019-07-21 at 8 47 24 PM" src="https://user-images.githubusercontent.com/43913398/61593090-ca8d2e80-abf8-11e9-8682-f3c585985b19.png">
 <img width="1440" alt="Screenshot 2019-07-21 at 8 49 23 PM" src="https://user-images.githubusercontent.com/43913398/61593110-0aecac80-abf9-11e9-8bc1-139ccf8c6c60.png">
 
 and more can be seen @ https://flairofreddit.herokuapp.com

# DATABASE

I have scrapped 2 databases - <br>
1. for DATA ANALYSIS - (4 months - from June 1st 2018 to October 1st 2018) containing a lot of fields like No_of_comments, timestamp, upvotes, etc.
2. for TRAINING & TESTING - (1 year - from June 1st 2018 to July 17st 2019) containg only Title, Body and flair.

URL of databases - 
1. <Strong> Mongodb (.json & .bson) </Strong> - <a href="https://github.com/Himanshu-Garg/Reddit-flair-detection/tree/master/other/mongodb%20database"> here </a>
2. <Strong> .csv file </Strong> - <a href="https://github.com/Himanshu-Garg/Reddit-flair-detection/tree/master/other/extracted_data"> here </a>


# Files STRUCTURE

Brief description of role of each file in the repo.
<ul>
 <li> <Strong> Other </Strong> 
    <ol>
      <li><Strong> Extracted_data - </Strong> contains .csv file of the extracted data (data.csv - 4 months data, original_1_year_data.csv - 1 year data)</li>
      <li><Strong> images - </Strong> contains images of data analysis made using "data analysis.ipynb"</li>
      <li><Strong> models - </Strong> contains saved models and vectors</li>
      <li><Strong> mongodb database - </Strong> contains mongodb database (.json and .bson) of extracted data</li>
      <li><Strong> 1year_data.ipynb - </Strong> used to extract 1 year data for training</li>
      <li><Strong> 4months_data.ipynb - </Strong> used to extract 4 months data for analysis</li>
      <li><Strong> data analysis.ipynb - </Strong> used for data analysis</li>
      <li><Strong> title.ipynb - </Strong> NLP only on title column of 1 year data </li>
     <li><Strong> title+body.ipynb - </Strong> NLP  on body+title columns of 1 year data </li>
     
   </ol> </li> <br>
 
 
 <li> <Strong> website </Strong> <br>
  Contains the full website that has been hosted on heroku - https://flairofreddit.herokuapp.com
    <ol>
      <li><Strong> model - </Strong> finally used model for flair prediction </li>
      <li><Strong> static - </Strong> contains images of data analysis</li>
      <li><Strong> templates - </Strong> contains .html file</li>
      <li><Strong> venv - </Strong> for creating virtual env named "venv"</li>
      <li><Strong> Procfile - </Strong> so heroku can detect that it's an app</li>
      <li><Strong> app.py - </Strong> for setting up flask (backend) </li>
      <li><Strong> requirements.txt - </Strong> contains names of all the dependencies required to rub the app</li>
     
   </ol> </li> <br>
   
 <li> <Strong> README.md </Strong></li>
</ul>


# APPROACH that I have followed...

I have finally used "TITLE" field only to predict the flair as, Body is not available in more than 50% posts (as shown in data analysis) and a lot of times, comments can be misleading and diverting, which can reduce the accuracy of the model.

I have trained the model on basically 4 algo - <Strong> Linear SVM, Logistic regression, Random forest classifier,  Multinomial NAIVE- BAYES </Strong> whose accuracy results are given below. I am using CountVector with TFIDF.

<Strong> NOTE - </Strong> For other factors like F1 score, Recall, Confusion Matrix, etc can be viewed from the respective .ipynb files.

<ul>
<li>accuracy for <Strong> TITLE only </Strong>
 <ol>
    <li>Linear SVM - 58.27%</li>
    <li>Random forest classifier - 56.29%</li>
    <li>Multinomial NAIVE- BAYES - 54.25% </li></ol></li>
<li>accuracy for <Strong> TITLE only </Strong> (WITH UNDERSAMPLING) 
  <ol>
    <li>Linear SVM - 48.38%</li>
    <li>Random forest classifier - 44.71%</li>
    <li>Multinomial NAIVE- BAYES - 56.69%</li> </ol></li>
</ul>

<br>

<ul>
<li>accuracy for <Strong> TITLE+BODY  </Strong>
 <ol>
    <li>Linear SVM - 58.27%</li>
    <li>Random forest classifier - 56.05%</li>
    <li>Logistic regression - 61%</li>
    <li>Multinomial NAIVE- BAYES - 55.61% </li></ol></li>
<li>accuracy for <Strong> TITLE+BODY </Strong> (WITH UNDERSAMPLING) 
  <ol>
    <li>Linear SVM - 49.2%</li>
    <li>Random forest classifier - 44.35%</li>
    <li>Logistic regression - 55.97%</li>
    <li>Multinomial NAIVE- BAYES - 55.97%</li> </ol></li>
</ul>


<Strong><i> 
Since, in unbalanced data, only Accuracy cannot be a factor to decide the best model. <br>
 So, after looking at F1 score and confusion matrix, Linear SVM (Title only - NO undersampling) model has been finalized and used in the website.
</Strong></i> 

Here are some of the manually tested data on the final model.
<img width="1029" alt="Screenshot 2019-07-22 at 3 25 08 PM" src="https://user-images.githubusercontent.com/43913398/61625238-d976ee00-ac97-11e9-9f5f-d94137d8e0fc.png">
