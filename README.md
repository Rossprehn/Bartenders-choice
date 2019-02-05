# Bartenders-Choice
![hero](https://i.imgur.com/zqS51Im.png)

## User Experience


A user opens the web app and is presented with an drink name name, ingredients, cocktail image, and a recipe on how to make the drink. If there are any comments associated with that drink they will display next to the the recipe. The user has the ability to add a new comment, change a comment, and delete comment. The user can also make a donation.

## Installation Instructions


Using the app does not require any installation, just visit https://bartenders-choice-5693a.firebaseapp.com. You are also free to use the source code for both the fronted of this app, located in this repository, and the backend of this app, located in the backend [here](https://github.com/Rossprehn/drinks). To install the backend please visit the other repository. To install the frontend please follow these installation instructions:

## Build Setup

``` 
install dependencies
npm install

serve with hot reload at localhost:8080
npm run dev

build for production with minification
npm run build

build for production and view the bundle analyzer report
npm run build --report
```

Vue: If you need help with Vue visit the Vue docs. For a detailed explanation on how vue-cli works, check out the guide and docs for vue-loader.

Stripe: In order to use the stripe functionality of this app you will need to create a stripe account here. From there you will need to click on your dashboard and then find your publishable key and secret key, which should be located under the API menu on the lift hand side. You will then need to include these keys in the code you cloned, the secret key goes in the backend .env file you will need to make and the publishable key goes in the frontend Donation component. You can find the stripe docs here

## Technologies

Vue.js, JavaScript, HTML, CSS, Stripe

##Author 

[Ross Prehn](https://github.com/Rossprehn)
