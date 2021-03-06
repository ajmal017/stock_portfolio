# VALIANT: A Web-based Stock Portfolio Trading Platform

With Valiant, a user is able to create an account, login and start trading with stocks available on the U.S. Stock Market. On the profile page, there is a grid that shows the user's current stocks, number of holdings, current price, and day change of their respective stocks. There is also an interface for the user to buy or sell stocks given the stock symbol and the quantity of shares. The transaction history page displays a log of all actions made by the user of the platform.

[Instructions for Running VALIANT locally](https://github.com/brianhe12/stock_portfolio#instructions-for-running-valiant-locally)

***IMPORTANT: When trying to visit the Valiant website, please wake up the [back-end server](http://stock-portfolio-flask.herokuapp.com/) first by visiting the page and letting it load. Then go on the [platform](https://valiant-stock-portfolio.herokuapp.com/) and begin trading. The reason we have to do this is because both the front-end and the back-end are hosted on [Heroku](http://heroku.com/), [which falls asleep after 30 minutes of inactivity](https://devcenter.heroku.com/articles/free-dyno-hours#dyno-sleeping). Both the front-end and the back-end have to be awake for correct functionality.*** 

<p align="center">
  <img src = "my-app/src/images/login.JPG">
  <img src = "my-app/src/images/profile_page.JPG">
  <img src = "my-app/src/images/transaction_history.JPG">
</p>

### Built with

* **Front-end:** Reactjs

* **Back-end:** Python Flask

* **Database:** MongoDB Atlas

* **Authentication:** Firebase

### System Diagram:
<p align="center">
  <img src = "my-app/src/images/stock_portfolio.png">
</p>

I used Flask as a REST API with React consuming the API by sending HTTP requests to it. On Flask, I had various endpoints that would return data in a JSON format to React when fetched. This data would then be displayed in a corresponding format on the front-end. 

I chose to use MongoDB Atlas for the database due to the fact that it is a noSQL database, which is easier to scale with lots of data and is faster for most operations than say mySQL or PostgreSQL. MongoDB is responsible for sending the correct data to the front-end depending on the user who is signed in.

Firebase provides an easy way to store and authenticate active users. This helped save time to work on other features of the web platform. It also allowed us to be able to receive analytical and demographical information of our users.

### Dependencies added 

npm install --save firebase

npm install --save react-router

npm install react-router-dom

npm install bootstrap

npm install reactstrap

npm install --save ag-grid-community ag-grid-react react-dom-factories

### Current pip is version 19.2.3
pip install flask

pip install pymongo

pip install pymongo[srv]

pip install python-dotenv

pip install -U flask-cors

pip install requests

# Instructions for running VALIANT locally

Developed with Node v11.3.0 and Python 3.8.1 on Windows 10 OS. Please have both Node and Python installed before proceeding. To find your personal node and python versions, run commands:

```
node -v
python -v
```
[Node Download link](https://nodejs.org/en/download/)

[Python Download Link](https://www.python.org/downloads/)

### Create these two .env's for in these following directories directories. You will have to generate your own API keys.

This first .env file holds my [Firebase Authentication](https://firebase.google.com/) keys. 
```
# stock_portfolio/my-app/.env 
REACT_APP_FIREBASE_KEY=************
REACT_APP_FIREBASE_AUTH_DOMAIN=************
REACT_APP_FIREBASE_DATABASE_URL=************
REACT_APP_FIREBASE_PROJECT_ID=************
REACT_APP_FIREBASE_STORAGE_BUCKET=************
REACT_APP_FIREBASE_MSG_SENDER_ID=************
REACT_APP_FIREBASE_APP_ID=************
REACT_APP_FIREBASE_MEASUREMENT_ID=************
```

This second .env file holds keys to connect to my [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) server and the keys for [IEX Cloud API](https://iexcloud.io/). 
```
# stock_portfolio/my-app/src/server/.env
MONGO_STRING="************"
IEX_TOKEN="************"
```

### Run the following commands to install dependencies.

### Front-end
```
# stock_portfolio/my-app
npm install
```

### Back-end 
```
# Run in root directory where requirements.txt is located: stock_portfolio/
pip install -r requirements.txt 
```


### Now we are ready to start up the back-end and front-end servers! Run the following two commands below in their following directories!

### Front-end 
```
# stock_portfolio/my-app
npm start
```

### Back-end 

```
# stock_portfolio/my-app/src/server
python flask_py.py
```

<p align="center">
  <img src = "my-app/src/images/server_start.JPG">
</p>

http://localhost:3000/login should automatically run in your browser but if it doesn't, please click the link.

***Please run on Google Chrome. Internet Explorer seems to have issues rendering. Thank you!***

### A few things I would like to improve on:
* A more responsive CSS, with ability to adjust to many different screen sizes. Users may have to zoom out a bit if their screen size is too small for the application :(.
* Fix the refresh on Buy/Sell function. I believe that a more seamless transition from buying/selling a stock to the neutral state of displaying the portfolio chart will improve user experience.
* Though functionality works, it would be better user experience to show error messages for when users do something invalid (e.g. Buy a stock that is too expensive, Try to buy using an invalid ticker, etc.)
* Because I am using Heroku server free tier, the website will fall asleep when there is 30 minutes of no activity. Start up after the server falls asleep will take a bit of time. Hosting on a paid service would solve this issue.




