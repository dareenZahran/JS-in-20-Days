# JavaScript Event Handling, Conditionals, Map and Filter Methods, and Doggos Quiz Game

This README file provides a summary of the JavaScript lessons on event handling, conditionals, map and filter methods, and building a Doggos Quiz Game. Here's a brief overview of each topic:

## Event Handling
JavaScript allows us to respond to user actions, such as clicks, keypresses, or mouse movements, through event handling. We can attach event handlers to HTML elements and define functions to be executed when those events occur. This enables us to create interactive and dynamic web pages.

## Conditionals
JavaScript conditionals allow us to make decisions in our code based on different conditions. Using if statements, else statements, and else if statements, we can define different code blocks to execute depending on the outcome of a condition. Conditionals help control the flow of our program and make it more flexible and adaptable.

## Map and Filter Methods
JavaScript provides powerful array methods like map and filter. The map method allows us to create a new array by transforming each element of an existing array using a provided function. The filter method, on the other hand, allows us to create a new array that contains only the elements satisfying a specific condition defined by a provided function. These methods enable us to perform complex operations on arrays in a concise and efficient manner.

## examples
```javascript
<!DOCTYPE html>

<html lang="en-US">

<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">

    <title>Quiz.js</title>
    <style>
        body {
            margin: 1rem auto;
            padding: 3rem;
            font-family: sans-serif;
        }

        header {
            width: 50%;
            margin: 1em auto;
        }

        main {
            min-width: 25rem;
            max-width: 50%;
            margin: 0px auto;
            display: flex;
            flex-direction: column;
        }

        #statement {
            border: 1px solid black;
            border-radius: 0.5rem;
            box-shadow: 5px 5px 5px gray;
            padding: 1rem;
            font-size: x-large;
            text-align: center;
            margin: 1rem 0px;
            min-height: 2em;
        }

        #explanation {
            padding: 1rem;
            text-align: center;
        }

        #options {
            width: 100%;
            display: flex;
            flex-direction: column;
        }

        button {
            padding: 0.5rem;
            font-size: medium;
            border-radius: 5px;
        }

        .correct {
            background-color: lightgreen;
        }

        .incorrect {
            background-color: lightpink;
        }
    </style>
</head>

<body data-new-gr-c-s-check-loaded="14.1114.0" data-gr-ext-installed="">
    <header>
        <h1>Quiz.js</h1>
        <p>Do you know JS? Find out!</p>
    </header>

    <main>
        <div id="statement">

        </div>

        <div id="options">
            <button name="true" value="true">true</button>
            <button name="false" value="false">false</button>
        </div>

        <button>Check your answer</button>

        <div id="explanation">

        </div>

    </main>

    <script type="text/javascript">

        // TODO 1: Declare & assign variables pointing to the corresponding element(s)
        // statement should be the "statement" div
        // optionButtons should be all the elements within the "options" div
        // explanation should be the "explanation" div
        const statement = document.getElementById("statement");
        const optionButtons = document.querySelector("#options").children;
        const explanation = document.getElementById("explanation");

        // TODO 2: Declare & assign a variable called fact
        // Its value should be an object with a statement, true/false answer, and explanation 

        const fact = {
            statement: "String is not a built-in object",
            answer: false,
            explanation: "String is a primitive data type, not a built-in object"
        }

        // TODO 3: Set the text of the statement element to the fact's statement
        statement.textContent = fact.statement;

        // TODO 4: Declare disable & enable functions to set or remove the "disabled" attribute from a given button element
        // disable(button) should set the button element's attribute "disabled" to the value ""
        // enable(button) should remove the attribute "disabled" from the button element
        const disable = (button) => {
            button.setAttribute("disabled", "");
        }

        const enable = (button) => {
            button.removeAttribute("disabled");
        }

        // TODO 5: Declare an isCorrect function that compares a guess to the right answer
        // isCorrect(guess) should return true if the guess matches the fact's answer
        function isCorrect(guess) {
            return guess === fact.answer;
        }

        // TODO 6A: Use a for loop to add a click event listener to each of the optionButtons
        for (let button of optionButtons) {
            button.addEventListener("click", (event) => {

                // TODO 6B: Within the event handler function, display the fact's explanation by setting the text of the explanation element
                explanation.textContent = fact.explanation;

                // TODO 7: Within the event handler function, 
                // Use a for loop to disable all the option buttons
                for (let button of optionButtons) {
                    disable(button);
                }

                // TODO 8: Within the event handler function,
                // Get the guessed value from the clicked button
                // Use a conditional to compare the guess to the fact's answer
                // and add the "correct"/"incorrect" class as appropriate
                const guess = event.target.value;
                if (isCorrect(guess)) {
                    event.target.classList.add("correct");
                } else {
                    event.target.classList.add("incorrect");
                }
            });
        }

    </script>
</body>

</html>
```
### Doges quiz 
```javascript
<!DOCTYPE html>
<!-- saved from url=(0067)https://anjana.dev/javascript-first-steps/3-doggofetch-starter.html -->
<html lang="en-US"><head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Doggo Fetch</title>
    <style>
        body {
            margin: 1rem auto;
            padding: 3rem;
            font-family: sans-serif;
        }
        header {
            width: 70%;
            margin: 1em auto;
        }
        main {
            max-width: 70%;
            margin: 0px auto;
            display:flex; 
            flex-direction: column;
        }
        img {
            max-width: 100%;
        }
        #image-frame {
            font-size: x-large;
            text-align: center;
            margin: 1rem auto;
        }
        #explanation, #score {
            padding: 1rem;
            text-align: center;
        }
        #options {
            max-width: 100%;
            display: flex;
            flex-direction: column;
        }
        button {
            padding: 0.5rem;
            font-size: medium;
            border-radius: 5px;
        }
        .correct {
            background-color: lightgreen;
        }
        .incorrect {
            background-color: lightpink;
        }
        .hidden {
            display: none;
        }
    </style>
  </head>
  <body data-new-gr-c-s-check-loaded="14.1114.0" data-gr-ext-installed="">
    <header>
    <h1>Guess the Doggo</h1>
    <p>What breed is the dog in this image?</p>

    </header>

    <main>
    <div id="image-frame">
    </div>
    <div id="options">
    </div>

    </main>

  


  <script type="module">

    const RANDOM_IMG_ENDPOINT = "https://dog.ceo/api/breeds/image/random";

    const BREEDS = ["affenpinscher", "african", "airedale", "akita", "appenzeller", "shepherd australian", "basenji", "beagle", "bluetick", "borzoi", "bouvier", "boxer", "brabancon", "briard", "norwegian buhund", "boston bulldog", "english bulldog", "french bulldog", "staffordshire bullterrier", "australian cattledog", "chihuahua", "chow", "clumber", "cockapoo", "border collie", "coonhound", "cardigan corgi", "cotondetulear", "dachshund", "dalmatian", "great dane", "scottish deerhound", "dhole", "dingo", "doberman", "norwegian elkhound", "entlebucher", "eskimo", "lapphund finnish", "bichon frise", "germanshepherd", "italian greyhound", "groenendael", "havanese", "afghan hound", "basset hound", "blood hound", "english hound", "ibizan hound", "plott hound", "walker hound", "husky", "keeshond", "kelpie", "komondor", "kuvasz", "labradoodle", "labrador", "leonberg", "lhasa", "malamute", "malinois", "maltese", "bull mastiff", "english mastiff", "tibetan mastiff", "mexicanhairless", "mix", "bernese mountain", "swiss mountain", "newfoundland", "otterhound", "caucasian ovcharka", "papillon", "pekinese", "pembroke", "miniature pinscher", "pitbull", "german pointer", "germanlonghair pointer", "pomeranian", "medium poodle", "miniature poodle", "standard poodle", "toy poodle", "pug", "puggle", "pyrenees", "redbone", "chesapeake retriever", "curly retriever", "flatcoated retriever", "golden retriever", "rhodesian ridgeback", "rottweiler", "saluki", "samoyed", "schipperke", "giant schnauzer", "miniature schnauzer", "english setter", "gordon setter", "irish setter", "sharpei", "english sheepdog", "shetland sheepdog", "shiba", "shihtzu", "blenheim spaniel", "brittany spaniel", "cocker spaniel", "irish spaniel", "japanese spaniel", "sussex spaniel", "welsh spaniel", "english springer", "stbernard", "american terrier", "australian terrier", "bedlington terrier", "border terrier", "cairn terrier", "dandie terrier", "fox terrier", "irish terrier", "kerryblue terrier", "lakeland terrier", "norfolk terrier", "norwich terrier", "patterdale terrier", "russell terrier", "scottish terrier", "sealyham terrier", "silky terrier", "tibetan terrier", "toy terrier", "welsh terrier", "westhighland terrier", "wheaten terrier", "yorkshire terrier", "tervuren", "vizsla", "spanish waterdog", "weimaraner", "whippet", "irish wolfhound"];

    
    // Utility function to get a randomly selected item from an array
    function getRandomElement(array) {
        const i = Math.floor(Math.random() * array.length);
        return array[i];
    }

    // Utility function to shuffle the order of items in an array in-place
    function shuffleArray(array) {
        return array.sort((a,b) => Math.random() - 0.5);
    }


// TODO 1
// Given an array of possible answers, a correct answer value, and a number of choices to get,
// return a list of that many choices, including the correct answer and others from the array
function getMultipleChoices(n, correctAnswer, array) {
  const choices = [correctAnswer]; // Include the correct answer in the choices array
  while (choices.length < n) {
    const randomChoice = getRandomElement(array);
    if (!choices.includes(randomChoice)) {
      choices.push(randomChoice);
    }
  }
  return shuffleArray(choices);
}

// TODO 2
// Given a URL such as "https://images.dog.ceo/breeds/poodle-standard/n02113799_2280.jpg"
// return the breed name string as formatted in the breed list, e.g. "standard poodle"
function getBreedFromURL(url) {
  const parts = url.split("/");
  const breed = parts[parts.length - 2];
  return breed.replace("-", " ");
}

// TODO 3
// Given a URL, fetch the resource at that URL, 
// then parse the response as a JSON object,
// finally return the "message" property of its body
async function fetchMessage(url) {
  const response = await fetch(url);
  const data = await response.json();
  return data.message;
}

// TODO 4
// For each of the choices in choicesArray,
// Create a button element whose name, value, and textContent properties are the value of that choice,
// attach a "click" event listener with the buttonHandler function,
// and append the button as a child of the options element
choicesArray.forEach((choice) => {
  const button = document.createElement("button");
  button.name = choice;
  button.value = choice;
  button.textContent = choice;
  button.addEventListener("click", buttonHandler);
  options.appendChild(button);
});

// TODO 5
// Asynchronously call the loadQuizData() function,
// Then call renderQuiz() with the returned imageUrl, correctAnswer, and choices
loadQuizData().then(([imageUrl, correctAnswer, choices]) => {
  renderQuiz(imageUrl, correctAnswer, choices);
});



  </script>

</body><grammarly-desktop-integration data-grammarly-shadow-root="true"><template shadowrootmode="open"><style>
  div.grammarly-desktop-integration {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
    -moz-user-select: none;
    -webkit-user-select: none;
    -ms-user-select:none;
    user-select:none;
  }

  div.grammarly-desktop-integration:before {
    content: attr(data-content);
  }
</style><div aria-label="grammarly-integration" role="group" tabindex="-1" class="grammarly-desktop-integration" data-content="{&quot;mode&quot;:&quot;full&quot;,&quot;isActive&quot;:true,&quot;isUserDisabled&quot;:false}"></div></template></grammarly-desktop-integration></html>
```
## Coding Exercises

### [Use Multiple Conditional (Ternary) Operators](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/use-multiple-conditional-ternary-operators)
```javascript
function checkSign(num) {
  return num === 0 ? "zero" : num > 0 ? "positive" : "negative";
}

checkSign(10);


```
### [Golf Code](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/golf-code)

```javascript
const names = ["Hole-in-one!", "Eagle", "Birdie", "Par", "Bogey", "Double Bogey", "Go Home!"];

function golfScore(par, strokes) {


if(strokes === 1){
  return "Hole-in-one!";
}else if(strokes <= par - 2){
return "Eagle" ;
}else if(strokes <= par - 1){
  return "Birdie";
}else if(strokes === "par"){
return "par";
}else if(strokes == par + 1)
  return "Bogey";
}else if(strokes == par + 2){
return "Double Bogey"
}else if(strokes >= par + 3)
return "Go Home!"
golfScore(5, 4);
```
### [Use the map Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-map-method-to-extract-data-from-an-array)

```javascript
const ratings = [];
for (let i = 0; i < watchList.length; i++) {
  ratings.push({title: watchList[i]["Title"], rating: watchList[i]["imdbRating"]});
}
const ratings = watchList.map(({ Title, imdbRating }) => ({ title: Title, rating: imdbRating }));

```
### [Use the filter Method to Extract Data from an Array](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/functional-programming/use-the-filter-method-to-extract-data-from-an-array)

```javascript
const filteredList = watchList
  .filter(movie => parseFloat(movie.imdbRating) >= 8.0)
  .map(({ Title, imdbRating }) => ({ title: Title, rating: parseFloat(imdbRating) }));

console.log(filteredList);

```
