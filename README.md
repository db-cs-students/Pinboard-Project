# Pinboard Project

**Note:** This project has been adapted from the official Repl.it Docs. Much of the content has been updated to include use of GitHub and GitFlow.

**Table of Content**

- [Getting Started](#getting-started)
  - [Planning](#planning)
  - [Opening the project on Repl.it](#opening-the-project-on-replit)
  - [Connecting the project to GitHub](#connecting-the-project-to-github)
  - [Starting a feature branch](#starting-a-feature-branch)
- [Skeleton](#skeleton)
  - [Adding the HTML skeleton](#adding-the-html-skeleton)
    - [HTML Boilerplate](#html-boilerplate)
    - [Commit Your Changes](#commit-your-changes)
  - [Adding styling](#adding-styling)
    - [Commit Your Changes](#commit-your-changes-1)
- [Writing data to your HTML](#writing-data-to-your-html)
  - [Update the skeleton](#update-the-skeleton)
    - [Start a new branch](#start-a-new-branch)
    - [Changing the card container](#changing-the-card-container)
    - [Commit Your Changes](#commit-your-changes-2)
  - [Using Javascript to render a card](#using-javascript-to-render-a-card)
  - [Filtering through the tags](#filtering-through-the-tags)
  - [Adding a modal](#adding-a-modal)
  - [Create a new card with custom input data](#create-a-new-card-with-custom-input-data)
- [Make It Your Own](#make-it-your-own)
  - [Some ideas of enhancing your project](#some-ideas-of-enhancing-your-project)
    - [Get photos using the Unsplash API](#get-photos-using-the-unsplash-api)
    - [Searching for multiple tags at once](#searching-for-multiple-tags-at-once)
    - [Suggest tags as you type](#suggest-tags-as-you-type)
- [Submitting](#submitting)

# Getting Started

The goal of this project is to create a "pinboard" of images that you can collect, categorize with tags and reflect on later.

You will be able to create new cards with custom tags and then filter tags via the search bar or by clicking on a tag.

![Example of the Moodboard functionality. You can add a new card, search tags and filter by tag buttons.](https://replit-docs-images.util.repl.co/images/teamsForEducation/pinboard-project/pinboard.gif)

## Opening the project

You'll need to migrate this code to Gitea. In the repository, you will find the basic files needed for our front-end web project. Open each of the files but don't make any changes yet. Note the purpose of each file and the exension used.

```yaml
index.html # Renders the document
style.css # Styling for the HTML
script.js # Updates HTML based on interactions
data.json # Initial data for pins
```

## Starting a feature branch

Now that you have migrated and cloned your repository, you need to start a new branch to begin working. This is the first step in the GitFlow. Let's call this initial branch `feature/skeleton`. Once you have switch to the feature branch, move on to make the first changes to your app.

# Skeleton

## Adding the HTML skeleton

We'll start off with a basic HTML skeleton, hard-coding the elements in our wireframe, which we are going to populate with data later on in this tutorial.

Open the `index.html` file and update the contents. While it is tempting to copy and paste, this will hold you back later on. Instead use the HTML alread present in the file. Read through the code below, and update the code in the `index.html` with what is missing.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>My Pinboard</title>
  </head>

  <body>
    <h1 class="header">My Pinboard</h1>
    <div class="searchContainer">
      <label class="searchLabel">search</label>
      <input class="searchInput" />
      <p class="searchResult"></p>
      <button class="newCardButton">Add a card</button>
    </div>
    <div class="cardContainer">
      <div class="card">
        <img />
        <div class="tagContainer">
          <button class="tagButton">tagButton</button>
        </div>
      </div>
    </div>
  </body>
</html>
```

### HTML Boilerplate

Above we have our basic HTML skeleton that we will expand throughout this tutorial to get to our final product. In addition to the markup for the project, it includes HTML boilerplate code. All HTML documents should include:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Title</title>
  </head>
  <body>
    <!-- Content of the Site -->
  </body>
</html>
```

Now that you have added the HTML skeleton, let's run a simple server to test our website. Open terminal and navigate to your project folder.

```bash
python -m http.server 3000
```

Open your web browser and navigate to `http://localhost:3000`. You should see our basic HTML form.

Now that you have added a basic skeleton, commit your changes using the message 'Update index with html skeleton'

## Adding styling

After writing our initial HTML, we need to start adding some styling to make it pretty and add some interactivity such as hover animations.

Copy the styling from [this CSS file](https://github.com/replit/replit.github.io/tree/master/static/tutorial-files/PinboardProject/style.css) into the file called `style.css`.

Let's link to the stylesheet in our `index.html` file by adding the following code within our `<head/>` below the `<title/>`.

```html
<link rel="stylesheet" href="style.css" />
```

While we're at it, let's add some pretty fonts.

[Google Fonts](https://fonts.google.com/) is a great resource for typography. You can choose the fonts you like, copy the `<link>` url and paste it in the `<head/>` of your `index.html` file.

We chose the font family "Bungee Shade" for the heading and family "Montserrat" for the body text. After adding the font links to the `index.html` file our `<head/>` now looks like this.

```html
<head>
  <meta charset="utf-8" />
  <title>My Moodboard</title>
  <link rel="stylesheet" href="style.css" />
  <link rel="preconnect" href="https://fonts.gstatic.com" />
  <link
    href="https://fonts.googleapis.com/css2?family=Bungee+Shade&family=Montserrat:wght@300&display=swap"
    rel="stylesheet"
  />
</head>
```

In the `style.css` that you copied earlier we make use of the above mentioned fonts already. If you chose different fonts than ours you should update the `style.css` accordingly. You can do this by changing the `font-family:` to match the ones you chose, like the below example for the heading as "Bungee Shade".

```css
h1 {
  font-size: 4rem;
  text-align: center;
  font-family: "Bungee Shade", cursive;
  color: #fc47bb;
  text-shadow: 0 0 5px #fc47bb;
}
```

Save your changes, and check your page in the web browser. Did the style and fonts change?

### Commit Your Changes

Now that you have made your changes. Commit and push your code.

Now that you are finished with the features for the skeleton, let's merge the changes from your feature branch to your main branch. Checkout your main branch.

```bash
git checkout main
```

Now merge the changes:

```bash
git merge feature/skeleton
```

Your changes are now part of the main branch.

# Writing data to your HTML

Ideally, we'd like to dynamically populate our front end instead of needing to hard-code it into the HTML. We can do this by using the Javascript `fetch()` function to fetch the array in our `data.json` file and populate the card containers accordingly.

## Update the skeleton

### Start a new branch

Since we are starting a new feature, we need to use GitFlow and create a new branch. Create a new branch with an appropriate name.

### Changing the card container

In the `index.html` file, find the current `cardContainer` element that looks like below:

```html
<div class="cardContainer">
  <div class="card">
    <img />
    <div class="tagContainer">
      <button class="tagButton">tagButton</button>
    </div>
  </div>
</div>
```

And replace all of it with the following:

```html
<div class="cardContainer" id="cardContainer"></div>
```

This creates an empty card container, which we will dynamically fill with card data using Javascript.

Your `index.html` should now look like this:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>My Moodboard</title>
    <link rel="stylesheet" href="style.css" />
    <link rel="preconnect" href="https://fonts.gstatic.com" />
    <link
      href="https://fonts.googleapis.com/css2?family=Bungee+Shade&family=Montserrat:wght@300&display=swap"
      rel="stylesheet"
    />
  </head>

  <body>
    <h1 class="header">My Moodboard</h1>
    <div class="searchContainer">
      <label class="searchLabel">search</label>
      <input class="searchInput" />
      <p class="searchResult"></p>
      <button class="newCardButton">Add a card</button>
    </div>
    <div class="cardContainer" id="cardContainer"></div>
  </body>
</html>
```

Commit your changes.

## Using Javascript to render a card

In order to render a card with data from each object in the `data.json` file, we'll need to add some scripting. In this project we will use [Javascript](https://www.javascript.com/). We will be adding our Javascript code to the `script.js` file but before we do that let's add a `<script/>` element to the `index.html` file.

Similar to `style.css` we need to link to our `script.js` file within the `index.html` file.

Add the following code above the the closing `<body/>` tag:

```html
<script type="text/javascript" src="script.js"></script>
```

Now that we have linked our `script.js` file, we can start adding our Javascript code to it.

Open the `script.js` file and add the following code:

```javascript
const cardContainer = document.querySelector("cardContainer");
let cards = [];
fetch("data.json")
  .then(function (response) {
    return response.json();
  })
  .then(function (data) {
    cards = data;
    appendData(cards);
  })
  .catch(function (err) {
    console.log(err);
  });
```

Above we begin by selecting the `cardContainer`, which will house the cards we are about to render. Using the `fetch()` function, we set `cards = data`, where the data is received from the `data.json` file.

Next we want to create a separate card for each card object in the `data.json` file. We can accomplish this by adding a function with a `for` loop. `For` loops are useful when you want to run over the same code over and over, using different values. Like in our case where we want to "loop" through all the `json` objects and create a separate card for each.

Add the following function `appendData()` to the `script.js` file:

```javascript
function appendData(data) {
  var cardContainer = document.getElementById("cardContainer");
  cardContainer.innerHTML = "";

  for (var i = 0; i < data.length; i++) {
    var card = document.createElement("div");
    card.className = "card";
    cardContainer.appendChild(card);

    var img = document.createElement("img");
    img.src = data[i].src;
    card.appendChild(img);

    var tagContainer = document.createElement("div");
    tagContainer.className = "tagContainer";
    card.appendChild(tagContainer);

    const tagButtons = data[i].tags.map((tag) => {
      const tagButton = document.createElement("button");
      tagButton.innerHTML = tag;
      return tagButton;
    });
    for (const tagButton of tagButtons) {
      tagButton.className = "tagButton";
      tagContainer.appendChild(tagButton);
    }
  }
}
```

Above we create an `appendData()` function, which maps over all the objects within the `data.json` array using a `for` loop.

Specifically the code above:

1. Gets the element we want to transform with `getElementById`.
2. Loops through each object within the array where `i` represents the object.
3. Creates a new `div` element with `class="card"` and appends it to the `cardContainer`.
4. Creates an `img` element with a `src` value of `data[i].src`, which refers to the `src` object within our `data.json` file.
5. Creates another `div` element with `class="tagContainer"`.
6. Creates the individual tag buttons by mapping over the `data[i].tags` object within `data.json`, using the javascript function, `map()`. For each tag, we create a new button element with an `onClick()` function.

Note that we can set attributes such as class names, source tags and IDs directly within this function. For example, the following code would set a class name of `class="card"` on all cards created within the for loop.

```javascript
var card = document.createElement("div");
card.className = "card";
```

## Filtering through the tags

Now that we have cards with tags, we want to be able to filter these tags into collections. We can do this by taking user input and searching our tags for a match.

Lets update our `index.html` file so that we can pass the user input to the `filterTags()` function we are going to create next.

Replace the current `searchContainer` element that looks like this:

```html
<div class="searchContainer">
  <label class="searchLabel">search</label>
  <input class="searchInput" />
  <p class="searchResult"></p>
  <button class="newCardButton">Add a card</button>
</div>
```

With the following:

```html
<div class="searchContainer">
  <label class="searchLabel">search</label>
  <input
    type="text"
    id="searchInput"
    class="searchInput"
    oninput="filterTags()"
  />
  <p id="searchResult" class="searchResult"></p>
  <button id="newCardButton" class="newCardButton">Add a card</button>
</div>
```

Add the following function `filterTags()` to your `script.js` file, below the `appendData()` function.

```javascript
function filterTags() {
  var searchTerm = document.getElementById("searchInput").value;
  document.getElementById("searchResult").innerHTML =
    "You searched for: " + searchTerm;

  const searchTermLower = searchTerm.toLowerCase();

  const filteredCards = cards.filter((card) => {
    return (
      card.tags.find((tag) => {
        const tagLower = tag.toLowerCase();
        return tagLower.includes(searchTermLower);
      }) !== undefined
    );
  });
  appendData(filteredCards);
}
```

The code above:

1. Gets the value of the `searchInput` and displays it to the user within the `searchResult` element.
2. Transforms the user input as well as the tags to be lowercase to ensure that the tags match the search keys exactly.
3. Filters the cards based on whether the tags include the search term results.

Note how we can set the search term value to the user's input value in the search bar by finding `var searchTerm = document.getElementById("searchInput").value;`.

Additionally, we want to be able to filter the cards by clicking on one of the tags.

Add the following to your `appendData()` function, below the creation of the tagButton element `const tagButton = document.createElement("button");`.

```javascript
tagButton.onclick = () => {
  const filteredCards = cards.filter((card) => {
    return (
      card.tags.find((tag) => {
        return tag.includes(tagButton.innerHTML);
      }) !== undefined
    );
  });
  appendData(filteredCards);
};
```

The `onClick()` function filters the cards in the card container by checking which cards contain tags with the same innerHTML.

## Adding a modal

A modal is a variation of a popup that can display information or ask for user information, such as a sign-up form. In our case, we want to use a basic modal to get the data we need to add a new card to our collection.

Add the following modal HTML code below the `cardContainer` element in your `index.html` file.

```html
<div id="newCardModal" class="modal">
  <div class="modal-content">
    <!-- the X-button can be achieved by using the "&times;" entity -->

    <span class="close">&times;</span>
    <form>
      <label for="imgSrc">Image source</label>
      <input
        type="text"
        id="imgsrc"
        name="source"
        class="newCardInput"
        placeholder="Paste your image url here"
      />
      <label for="tags">Tags</label>
      <input
        type="text"
        id="tags"
        name="tags"
        class="newCardInput"
        placeholder="Separate tags with a semicolon ( ; )"
      />

      <button type="button" class="submitButton" onclick="saveNewCard()">
        Submit
      </button>
    </form>
  </div>
</div>
```

Within the modal, we use an HTML form element with a submit button. The input type specifies the type of user input we expect, which can be text, radio buttons, checkboxes, etc.

Your `index.html` file should now look like this:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>My Moodboard</title>
    <link rel="stylesheet" href="style.css" />
    <link rel="preconnect" href="https://fonts.gstatic.com" />
    <link
      href="https://fonts.googleapis.com/css2?family=Bungee+Shade&family=Montserrat:wght@300&display=swap"
      rel="stylesheet"
    />
  </head>

  <body>
    <h1 class="header">My Moodboard</h1>
    <div class="searchContainer">
      <label class="searchLabel">search</label>
      <input
        type="text"
        id="searchInput"
        class="searchInput"
        oninput="filterTags()"
      />
      <p id="searchResult" class="searchResult"></p>
      <button id="newCardButton" class="newCardButton">Add a card</button>
    </div>
    <div class="cardContainer" id="cardContainer"></div>
    <div id="newCardModal" class="modal">
      <div class="modal-content">
        <!-- the X-button can be achieved by using the "&times;" entity -->

        <span class="close">&times;</span>
        <form>
          <label for="imgSrc">Image source</label>
          <input
            type="text"
            id="imgsrc"
            name="source"
            class="newCardInput"
            placeholder="Paste your image url here"
          />
          <label for="tags">Tags</label>
          <input
            type="text"
            id="tags"
            name="tags"
            class="newCardInput"
            placeholder="Separate tags with a semicolon ( ; )"
          />

          <button type="button" class="submitButton" onclick="saveNewCard()">
            Submit
          </button>
        </form>
      </div>
    </div>
    <script type="text/javascript" src="script.js"></script>
  </body>
</html>
```

We still need to create a button to open and close the modal. We can do this by changing the display property of the button we create.

Add the following code to the end of your `script.js` file:

```javascript
var newCardButton = document.getElementById("newCardButton");

var newCardModal = document.getElementById("newCardModal");
newCardButton.onclick = function () {
  newCardModal.style.display = "block";
};

var closeModal = document.getElementsByClassName("close")[0];
closeModal.onclick = function () {
  newCardModal.style.display = "none";
};

window.onclick = function (event) {
  if (event.target == newCardModal) {
    newCardModal.style.display = "none";
  }
};
```

Above we create the button and set the display property to "block" (from a default of `display="none"`). To close the modal, we do the opposite, setting the display property back to `display="none"`. The `window.onclick` function will enable the modal to close when the user clicks anywhere outside of the modal body.

When clicking on the `Add a card` button, the modal form should appear and you should be able to close it by clicking the X at the top right, or anywhere outside of the modal contents.

## Create a new card with custom input data

Lastly, we need to use the user data that we collected from the modal inputs to create and append a new card to our collection.

Add the following code to the end of your `script.js` file.

```javascript
function saveNewCard() {
  var newImgSrc = document.getElementById("imgsrc").value;

  var newTags = document.getElementById("tags").value.split(";");

  var lastCardId = cards[cards.length - 1].id;

  var newCard = {
    id: lastCardId + 1,
    src: newImgSrc,
    tags: newTags,
  };

  cards = [...cards, newCard];
  appendData(cards);

  newCardModal.style.display = "none";
}
```

The above function will take the input from the user, correctly format it with a unique id, add it to our collection and close the modal.

Specifically the code:

1. Gets the new image source and saves it in the variable `newImgSrc`.
2. Separates the tag values with the Javasript `split()` function.
3. Creates a unique ID by getting the last ID in the existing array and adding one.
4. Creates a `newCard` variable that stores the new data in the same format as in the existing `data.json` format.
5. Adds a `newCard` to your existing card array.
6. Sets the modal display to `none` to close the modal.

### Commit and merge

Commit your changes. Checkout the main branch. Merge your feature branch with the main.

# Make It Your Own

Now you are ready to customize this project. Feel free to play around with the fonts and styling to make it your own. You can also update the data to change the purpose of this app.

Here are some customized pinboards based on this project with their own cards for your inspiration.

- [Home decor board](https://repl.it/@ritza/home-decor)
- [Recipe collection](https://repl.it/@ritza/recipe-board)
- [Travel wishlist](https://repl.it/@ritza/travel-todos)

## Some ideas of enhancing your project

### Get photos using the Unsplash API

[Unsplash](https://unsplash.com/developers) has a free JSON API that gives you access to thousands of high-quality photos that can easily be integrated to your project. After creating an account, follow the README.md instructions for the [official Javascript wrapper](https://github.com/unsplash/unsplash-js) and read their [documentation](https://unsplash.com/documentation) if you get stuck.

### Searching for multiple tags at once

You may want to search for more than one tag at a time, like searching "vegetarian" and "easy" recipes simultaneously. A hint for doing this is to split the search terms in a similar way to how we split the tags when adding them to the card.

### Suggest tags as you type

When you have a large number of tags, you may want to suggest existing tags to the user while they are typing in the search bar, using a drop-down list. To do this, you'll need to perform a fetch query while the user types, and populate your drop-down list with the all the possible tags that contain the search phrase.

# Submitting

After you have completed your project, push your code to Gitea.
